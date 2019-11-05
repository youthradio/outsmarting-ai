<template>
  <slide class="carousel-item-big">
    <div class="image-container">
      <img :src="carouselItemImgSrc" class="carousel-image">
    </div>
    <h3 class="carousel-title-underline" v-html="carouselItemTitle" />
    <p class="carousel-date" v-html="carouselDate" />
    </p>
  </slide>
</template>

<script>
export default {
  props: {
    carouselItemTitle: {
      type: String,
      require: true,
      default: null
    },
    carouselItemImgSrc: {
      type: String,
      require: true,
      default: null
    },
    carouselDate: {
      type: String,
      require: true,
      default: null
    }
  },
  data () {},
  computed: {},
  methods: {}
}
</script>

<style lang="scss" scoped>
@import "~@/css/vars";
@import "~@/css/base";
@import "~@/css/mixins";

.carousel-item-big{
    font-family: "Assistant";
    margin: 0.5rem 0.5rem 0.5rem 0rem;
    cursor: pointer;
}

.image-container{
    max-width: 100%;
    img{
      max-width: 100%; // 100 percent of 100 percent lol
    }
}

.carousel-title-underline{
    line-height: 0;
    padding: 1.2rem 0rem 1rem 0rem;
    border-bottom: 3px solid black;
}
</style>
