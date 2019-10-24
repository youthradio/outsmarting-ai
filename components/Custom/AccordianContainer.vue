<template>
  <article class="accordian" :class="accordianClasses">
    <div class="accordian-header" @click="toggleAccordion">
      <!-- <span v-html="{ accordianTitle }" /> 'works' but shoots out raw json markup and, as usual, isn't safe -->
      {{ accordianTitle }}<span class="accordianIcon" :class="accordianClasses" />
    </div>
    <div class="accordian-body">
      <div class="accordian-content">
        Test Content but much longer and filling up the space in the component
      </div>
    </div>
  </article>
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
.accordian{
    background-color: #00EBAB;
    color: black;
    padding: 0 0.3rem 0.3rem 0.3rem; // actually is just the content's border
    max-width: 100%;
}

.accordian-header{
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  padding: 0.4rem;
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
