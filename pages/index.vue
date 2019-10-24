<template>
  <div class="container">
    <HeaderContainer />
    <article>
      <AccordianContainer :accordian-title="articleData.sections[0].title" />
      <AccordianContainer :accordian-title="articleData.sections[1].title" />
      <AccordianContainer :accordian-title="articleData.sections[2].title" />
      <p v-html="articleData.leading" />
      <p v-html="articleData.leading2" />
      <p v-html="articleData.leading3" />
      <p>Vitae purus faucibus ornare suspendisse sed nisi. Dignissim cras tincidunt lobortis feugiat vivamus at. Lorem mollis aliquam ut porttitor. Mauris in aliquam sem fringilla ut morbi tincidunt augue. Lorem ipsum dolor sit amet. Nibh mauris cursus mattis molestie a iaculis at. Vulputate sapien nec sagittis aliquam malesuada bibendum. Viverra suspendisse potenti nullam ac tortor vitae purus faucibus. Interdum consectetur libero id faucibus nisl tincidunt eget. Vulputate enim nulla aliquet porttitor lacus luctus. Ornare arcu dui vivamus arcu felis bibendum ut tristique. Dignissim cras tincidunt lobortis feugiat vivamus at. Turpis massa tincidunt dui ut ornare lectus.</p>
      <p>Lobortis elementum nibh tellus molestie nunc non blandit massa. Elit duis tristique sollicitudin nibh sit amet commodo nulla facilisi. Semper eget duis at tellus at urna. Sed faucibus turpis in eu. Sit amet volutpat consequat mauris nunc. Libero volutpat sed cras ornare arcu dui. Ut pharetra sit amet aliquam id. Turpis egestas pretium aenean pharetra magna ac placerat vestibulum. Mi proin sed libero enim sed faucibus turpis in eu. Dui accumsan sit amet nulla facilisi morbi tempus. Leo a diam sollicitudin tempor. Nunc mi ipsum faucibus vitae aliquet nec ullamcorper sit amet. Consectetur libero id faucibus nisl tincidunt. In ornare quam viverra orci sagittis. Morbi tincidunt augue interdum velit euismod in pellentesque massa. Dolor sit amet consectetur adipiscing. Quisque id diam vel quam elementum pulvinar etiam non quam. Pellentesque elit eget gravida cum sociis natoque penatibus. Urna neque viverra justo nec ultrices dui sapien. Sed id semper risus in hendrerit gravida rutrum.</p>
      <MapContainer />
      <p>Arcu odio ut sem nulla pharetra diam sit amet. Non sodales neque sodales ut etiam sit amet nisl purus. Elementum nibh tellus molestie nunc non blandit massa enim. Non diam phasellus vestibulum lorem sed risus ultricies. Vel facilisis volutpat est velit egestas dui. Ut ornare lectus sit amet est placerat in egestas. Scelerisque viverra mauris in aliquam. Tortor posuere ac ut consequat semper viverra nam libero justo. Libero nunc consequat interdum varius sit. Scelerisque felis imperdiet proin fermentum leo vel orci porta. Ut eu sem integer vitae justo eget magna fermentum iaculis. Vitae sapien pellentesque habitant morbi tristique senectus. Elementum tempus egestas sed sed risus. Et sollicitudin ac orci phasellus egestas.</p>
      <p>In vitae turpis massa sed elementum tempus egestas. Eget mi proin sed libero enim sed faucibus. Nullam non nisi est sit amet facilisis magna etiam tempor. Arcu non sodales neque sodales ut etiam. Magna sit amet purus gravida quis blandit turpis. Ultricies mi quis hendrerit dolor magna eget est lorem. Euismod elementum nisi quis eleifend quam adipiscing vitae. Urna porttitor rhoncus dolor purus. Nec ullamcorper sit amet risus nullam eget. Mi tempus imperdiet nulla malesuada pellentesque elit. Vulputate mi sit amet mauris commodo quis imperdiet massa. Integer feugiat scelerisque varius morbi enim.</p>
    </article>
    <ShareContainer />
    <RelatedPostsContainer />
    <FooterContainer />
  </div>
</template>

<script>

import ArticleData from '../data/data.json'
import CommonUtils from '../mixins/CommonUtils'
import RelatedPostsContainer from '~/components/RelatedPosts/RelatedPostsContainer'
import MapContainer from '~/components/Map/MapContainer'
import HeaderContainer from '~/components/Header/HeaderContainer'
import AccordianContainer from '~/components/Custom/AccordianContainer'
import ShareContainer from '~/components/custom/ShareContainer'
import FooterContainer from '~/components/Footer/FooterContainer'

export default {
  components: {
    RelatedPostsContainer,
    MapContainer,
    HeaderContainer,
    ShareContainer,
    FooterContainer,
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

</style>
