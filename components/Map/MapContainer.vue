<template>
  <div
    v-observe-visibility="{
      callback: visibilityChanged,
      once: true,
    }"
    class="row"
  >
    <USAMap
      :map-data="mapData"
      :markers-data="markersData"
      :content-data="contentData"
      :loading-markers="loadingMarkers"
      :loading-map="loadingMap"
    />
  </div>
</template>

<script>
import { csvParse } from 'd3-dsv'
import USAMap from './USAMap.vue'

export default {
  name: 'MapContainer',
  components: {
    USAMap
  },
  data () {
    return {
      mapData: {},
      markersData: [],
      contentData: [],
      loadingMarkers: false,
      loadingMap: false,
      loadingData: false
    }
  },
  computed: {

  },
  created () {
    // this.loadMapData()
    // this.loadMarkersData()
    // this.loadContentData()
  },
  mounted () {

  },
  methods: {
    visibilityChanged () {
      this.loadMapData()
    },
    async loadMarkersData () {
      this.loadingMarkers = true
      this.markersData = await fetch('https://docs.google.com/spreadsheets/d/e/2PACX-1vSBL4rLXWCAs0GloIzk-WODWDiBBLBNVwwkmTPuKoYnVtMgE1-VtT_KhTX5SYJ2davMzwOUrqB2lWq6/pub?gid=304433033&single=true&output=csv')
        .then(res => res.text())
        .then(res => csvParse(res))
        .then((data) => {
          delete data.columns
          return data.map(e => ({
            geo: [parseFloat(e.long), parseFloat(e.lat)],
            address: e.Address
          }))
        })
      this.loadingMarkers = false
    },
    async loadContentData () {
      this.loadingData = true
      this.contentData = await fetch('    https://docs.google.com/spreadsheets/d/e/2PACX-1vQUEsaguvKunKdIYaLQnOzFuppgpTyQP3p9P_XTxLnaOFWwoEdIjmsdVYgNwWsJvjQKXteg74msIz_6/pub?gid=1657489261&single=true&output=csv')
        .then(res => res.text())
        .then(res => csvParse(res))
        .then((data) => {
          const years = data.columns.slice(2)
          return data.map(e =>
            ({
              abbr: e.Abbr,
              state: e.State,
              values: years.map(y => [y, e[y]])
            })
          )
        })
      this.loadingData = false
    },

    async loadMapData () {
      this.loadingMap = true
      this.mapData = await fetch('maps/all-states-light-500k.json')
        .then(res => res.json())
      this.loadingMap = false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '~@/css/_vars';

</style>
