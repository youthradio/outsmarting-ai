<template>
  <div>
    <article class="accordian" :class="accordianClasses">
      <div class="accordian-header" @click="toggleAccordion">
        <span class="titleSource" v-html=" accordianTitle " /> <span class="accordianIcon" :class="accordianClasses" />
      </div>
      <div class="accordian-border">
        <div class="accordian-body">
          <div class="accordian-content">
            <span class="bodySource" v-html=" accordianBody " />
          </div>
        </div>
      </div>
    </article>
  </div>
</template>

<script>
export default {
  props: {
    accordianTitle: {
      type: String,
      require: false,
      default: null
    },
    accordianBody: {
      type: String,
      require: true,
      default: null
    }
  },
  data () {
    return {
      isOpen: !true
    }
  },
  computed: {
    accordianClasses () {
      return {
        'is-closed': !this.isOpen,
        'is-primary': this.isOpen,
        'is-dark': !this.isOpen
      }
    }
  },
  methods: {
    toggleAccordion () {
      this.isOpen = !this.isOpen
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~@/css/mixins';
@import "~@/css/vars";

/deep/ .accordian-header h3 {
  padding: 0 !important;
  margin: 0;

  font-weight: 800;
  letter-spacing: 0.4px;
  font-size: 100%;
}
.accordian{
    color: black;
    padding: 0 0.3rem 0.3rem 0.3rem; // actually is just the content's border
    max-width: 100%;
}
.is-closed .accordian-border{
  transition: 0.2s ease all;
    background-color: #00EBAB;
    padding: 0rem;
}
.accordian-border{
    transition: 0.2s ease all;
    background-color: #00EBAB;
    padding: 0.3rem 0.3rem 0.3rem 0.3rem;
}
.accordian-header{
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  padding: 0.4rem;
  max-width: 50%;
  background-color: #00EBAB;
}

.is-closed .accordianIcon:after{
    content: '▾';
    position: relative;
    pointer-events: none;
}

.is-primary .accordianIcon:after{
    content: '▴';
    position: relative;
    pointer-events: none;
}

.is-closed .accordian-body{
  max-height: 0rem;
}

.is-primary .accordian-body{
    padding: 0.3rem;
}

.accordian-body{
    max-height: 10rem;
    background-color: $white;
    overflow-y: scroll;
    overflow-x: hidden;
    transition: 0.2s ease all;
}
</style>
