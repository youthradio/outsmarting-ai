<template>
  <carousel>
    <slide
      v-for="(carouselArticle, i) in testObjects"
      :key="`${carouselArticle}${i}`"
      class="carousel-item-big"
    >
      <div class="image-container">
        <img :src="carouselArticle.articleImg" class="carousel-image">
      </div>
      <h3 class="carousel-title-underline" v-html="carouselArticle.articleTitle" />
      <p class="carousel-date" v-html="carouselArticle.articleDate" />
      </p>
    </slide>
  </carousel>
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
  data () {
    return {
      testObjects: [

        { articleTitle: 'Title 1', articleDate: 'october 22', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 2', articleDate: 'may 42', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 3', articleDate: 'june 4', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 4', articleDate: 'oct 4', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 5', articleDate: 'june 4', articleImg: 'https://www.fillmurray.com/700/700' }

      ]
    }
  },
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
