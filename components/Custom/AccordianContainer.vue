<!-- eslint-disable vue/no-v-html  -->
<template>
  <div
    class="accordian"
    :class="accordianClasses"
  >
    <div
      class="accordian-header"
      @click="toggleAccordion"
    >
      <div
        class="title-source"
        v-html="accordianTitle"
      /> <span
        class="accordian-icon"
        :class="accordianClasses"
      />
    </div>
    <div class="accordian-border">
      <div class="accordian-body">
        <div class="accordian-content">
          <div
            class="body-source"
            v-html="accordianBody"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    accordianTitle: {
      type: String,
      require: true,
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
@import "~@/css/mixins";
@import "~@/css/vars";

/deep/ .accordian-header h3 {
  padding: 0 !important;
  margin: 0;

  font-weight: 800;
  letter-spacing: 0.4px;
  font-size: 100%;
}
.accordian {
  color: black;
  padding-top: 1rem;
}
.is-closed .accordian-border {
  transition: max-height 0.2s ease;
  background-color: $green;
  padding: 0rem;
}
.accordian-border {
  transition: max-height 0.2s ease;
  background-color: $green;
  padding: 0.3rem;
}
.accordian-header {
  cursor: pointer;
  display: inline-flex;
  justify-content: space-between;
  padding: 0.3rem;
  background-color: $green;
}
.body-source{
  padding: 0.4rem;
}

.is-closed .accordian-icon:after{
    font-family: 'yr-icons';
    font-size: 50%;
    content: "\e900";
    position: relative;
    pointer-events: none;
}

.is-primary .accordian-icon:after{
    font-family: 'yr-icons';
    font-size: 50%;
    content: "\e901";
    position: relative;
    pointer-events: none;
}

.is-closed .accordian-body {
  max-height: 0rem;
}

.is-primary .accordian-body {
  padding: 0rem;
}

.accordian-body {
  background-color: $white;
  overflow-x: hidden;
  transition: max-height 0.2s ease;
}
</style>
