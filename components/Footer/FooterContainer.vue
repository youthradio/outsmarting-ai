<template>
  <footer>
    <FooterMenu />
    <FooterEmailSubscribe />
  </footer>
</template>

<script>
import FooterEmailSubscribe from './FooterEmailSubscribe'
import FooterMenu from './FooterMenu'

export default {
  components: {
    FooterEmailSubscribe,
    FooterMenu
  }
}
</script>

<style scoped lang="scss">
footer{
  position: relative;
  margin-top: 1rem;
  z-index: 1000
}
</style>
