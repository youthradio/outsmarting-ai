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
        <AccordianContainer
          v-for="(article, i) in articleData.sections"
          :key="`${article}${i}`"
          :accordian-body="article.content"
          :accordian-title="article.title"
        />
        <h2 class="body-header" v-html="articleData.subleading" />
        <ol>
          <li
            v-for="item in articleData.wcyd"
            :key="item"
          >
            <div class="ul-title" v-html="item.title" />
            <p v-html="cleanPtags(item.content)" />
          </li>
        </ol>
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
    grid-template-columns: 2fr 1fr;
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
    order: 1;
  }
}

/deep/ .ul-title h3{
  padding: 0;
  font-size: 1rem;
  font-weight: 800;
  letter-spacing: 0.5px;
}
.body-header {
  width: 100%;
  border-bottom: 6px solid $green;
  padding: 1rem 0 0 0;
  line-height: 2rem;

  color: $green;
  font-family: "Days Sans", sans-serif;
  letter-spacing: 0;
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
