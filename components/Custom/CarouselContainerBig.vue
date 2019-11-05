<template>
  <carousel>
    <slide class="carousel-item-big">
      <div class="image-container">
        <img src="https://picsum.photos/900" class="carousel-image">
      </div>
      <h3 class="carousel-title-underline">
        Test Title
      </h3>
      <p class="carousel-date">
        Test Date 2019
      </p>
    </slide>
    <slide class="carousel-item-big">
      <div class="image-container">
        <img src="https://picsum.photos/900" class="carousel-image">
        <h3 class="carousel-title-underline">
          Test Title
        </h3>
        <p class="carousel-date">
          Test Date 2019
        </p>
      </div>
    </slide>
  </carousel>
</template>

<script>
export default {
  props: {},
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
    padding: 0.5rem 0.5rem 0.5rem 0rem;
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
