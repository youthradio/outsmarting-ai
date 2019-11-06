<!-- eslint-disable vue/no-v-html  -->
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
        <p
          v-for="leading in articleData.leadings"
          :key="leading"
          v-html="cleanPtags(leading)"
        />
        <CarouselContainerBig :core-data="testObjects1" per-page-num="2" />
        <CarouselContainerBig :core-data="testObjects2" small-items per-page-num="5" />
      </div>
      <div class="img-body">
        <img
          class="article-img"
          src="~/assets/images/article-bg.jpg"
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
import CarouselContainerBig from '~/components/Custom/CarouselContainerBig'
// import ShareContainer from '~/components/custom/ShareContainer'
// import FooterContainer from '~/components/Footer/FooterContainer'

export default {
  components: {
    // RelatedPostsContainer,
    // MapContainer,
    HeaderContainer,
    // ShareContainer,
    // FooterContainer,
    CarouselContainerBig
  },
  mixins: [
    CommonUtils
  ],
  data () {
    return {
      testObjects1: [

        { articleTitle: 'Title 1', articleDate: 'october 22', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 2', articleDate: 'may 42', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 3', articleDate: 'june 4', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 4', articleDate: 'oct 4', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 5', articleDate: 'june 4', articleImg: 'https://www.fillmurray.com/700/700' }

      ],
      testObjects2: [

        { articleTitle: 'Title 6', articleDate: 'october 22', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 7', articleDate: 'may 42', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 8', articleDate: 'june 4', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 9', articleDate: 'oct 4', articleImg: 'https://www.fillmurray.com/700/700' },
        { articleTitle: 'Title 10', articleDate: 'june 4', articleImg: 'https://www.fillmurray.com/700/700' }

      ]
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
  beforeMount () {
  },
  methods: {
    cleanPtags (string) {
      return string.replace(/<\/?p[^>]*>/g, '')
    }
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
    grid-template-columns: 1fr;
    grid-template-rows: 1fr;
  }
}
.main-body {
  order: 2;
  background-color: $white;
  padding-left: 2.5rem;
  padding-right: 2.5rem;
  p,
  div {
    padding-right: 1.5rem;
    margin-bottom: 0.4rem;
  }
  @include breakpoint(medium) {
    order: 2;
  }
}

.ul-title {
  font-family: "Assistant";
  line-height: 1rem;
  padding: 0.25rem 0 0 0;
  font-size: 1rem;
  font-weight: 800;
  letter-spacing: 0.5px;
}
.body-header {
  width: 100%;
  border-bottom: 6px solid $green;
  padding: 1rem 0 0 0;
  margin-bottom: 0.2rem;
  line-height: 2rem;

  color: $green;
  font-family: "Days Sans", sans-serif;
  letter-spacing: 0;

  /deep/ p{
  margin-bottom: 0.2rem;
  line-height: 2rem;
  }
}
.sub-header {
  display: inline-block;
  padding: 0.5rem 0.5rem;
  margin: 1rem 0rem 0rem 0rem;
  background-color: $green;

  color: #000;
  font-family: "Days Sans", sans-serif;
  letter-spacing: 0;
}
.img-body {
  order: 1;
  z-index: 0;
  @include breakpoint(medium) {
    order: 1;
  }
}
.article-img {
  position: relative;
  @include breakpoint(medium) {
  }
  width: 100vw;
  height: 50vh;
  object-fit: cover;
}

ol {
  list-style: none;
  counter-reset: yr-counter;
}

ol li {
  margin: 0 0 0.5rem 0;
  counter-increment: yr-counter;
  position: relative;
}

ol li:before{
  position: absolute;
  left: -1.3rem;
  content: counter(yr-counter) " ";
  color: $green;
  font-weight: bold;
}
</style>
