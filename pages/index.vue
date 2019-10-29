<template>
  <div class="container">
    <HeaderContainer />
    <div class="article-body">
      <div class="main-body">
        <h3 class="sub-header">
          COMING SOON
        </h3>
        <h2 class="body-header">
          OUTSMARTING AI
        </h2>
        <p v-html="articleData.leading" />
        <p v-html="articleData.leading2" />
        <p v-html="articleData.leading3" />
        <AccordianContainer
          v-for="article in articleData.sections"
          :key="article.content"
          :accordian-body="article.content"
          :accordian-title="article.title"
        />
      </div>
      <div class="img-body">
        <img
          class="article-img"
          src="~/assets/images/article-bg.png"
        >
      </div>
    </div>
    <!-- <ShareContainer /> -->
    <!-- <RelatedPostsContainer /> -->
    <!-- <FooterContainer /> -->
  </div>
</template>

<script>

import ArticleData from '../data/data.json'
import CommonUtils from '../mixins/CommonUtils'
// import RelatedPostsContainer from '~/components/RelatedPosts/RelatedPostsContainer'
// import MapContainer from '~/components/Map/MapContainer'
import HeaderContainer from '~/components/Header/HeaderContainer'
import AccordianContainer from '~/components/Custom/AccordianContainer'
// import ShareContainer from '~/components/custom/ShareContainer'
// import FooterContainer from '~/components/Footer/FooterContainer'

export default {
  components: {
    // RelatedPostsContainer,
    // MapContainer,
    HeaderContainer,
    // ShareContainer,
    // FooterContainer,
    AccordianContainer
  },
  mixins: [
    CommonUtils
  ],
  data () {
    return {

    }
  },
  computed: {
  },
  watch: {

  },
  asyncData (ctx) {
    return {
      articleData: ArticleData.content
    }
  },
  mounted () {
  },
  methods: {

  }
}
</script>

<style lang="scss" scoped>
@import "~@/css/vars";
@import "~@/css/base";
@import "~@/css/mixins";

.article-body {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 1fr;
  @include breakpoint(medium) {
    grid-template-columns: 2fr 1fr;
    grid-template-rows: 1fr;
  }
}
.main-body {
  order: 2;
  background-color: $white;
  padding-left: 1.5rem;
  padding-right: 1.5rem;
  p,
  div {
    padding-right: 1.5rem;
  }
  @include breakpoint(medium) {
    order: 1;
  }
}
.body-header {
  width: 100%;
  border-bottom: 6px solid $green;
  padding: 0;
  line-height: 2rem;

  color: $green;
  font-family: "Days Sans", sans-serif;
  letter-spacing: 0;
}
.sub-header {
  display: inline-block;
  padding: 0.5rem 0.5rem;
  margin: 0rem 0rem 1rem 0rem;
  background-color: $green;

  color: #000;
  font-family: "Days Sans", sans-serif;
  letter-spacing: 0;
}
.img-body {
  order: 1;
  z-index: 0;
  @include breakpoint(medium) {
    order: 2;
  }
}
.article-img {
  position: relative;
  @include breakpoint(medium) {
    position: fixed;
    width: auto;
    height: 100vh;
  }
  width: 100vw;
  height: 50vh;
  object-fit: cover;
}
</style>
