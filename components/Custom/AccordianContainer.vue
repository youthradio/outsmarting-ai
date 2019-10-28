<template>
  <div>
    <article class="accordian" :class="accordianClasses">
      <div class="accordian-header" @click="toggleAccordion">
        <div class="title-source" v-html=" accordianTitle " /> <span class="accordian-icon" :class="accordianClasses" />
      </div>
      <div class="accordian-border">
        <div class="accordian-body">
          <div class="accordian-content">
            <div class="body-source" v-html=" accordianBody " />
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
}
.is-closed .accordian-border{
    transition: 0.2s ease all;
    background-color: $green;
    padding: 0rem;
}
.accordian-border{
    transition: 0.2s ease all;
    background-color: $green;
    padding: 0.3rem 0.3rem 0.3rem 0.3rem;
}
.accordian-header{
  cursor: pointer;
  display: inline-block;
  justify-content: space-between;
  padding: 0.4rem;
  background-color: $green;
}

.is-closed .accordian-icon:after{
    content: '▾';
    position: relative;
    pointer-events: none;
}

.is-primary .accordian-icon:after{
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
    background-color: $white;
    overflow-x: hidden;
    transition: 0.2s ease all;
}
</style>
