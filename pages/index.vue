<template>
  <div style="background-color: #fafafa">
    <v-parallax
      src="https://images7.alphacoders.com/437/thumb-1920-437264.jpg"
      height="450"
    >
      <div style="background-color: rgba(0, 0, 0, 0.2)">
        <BaseLayout>
          <map-svg />
        </BaseLayout>
      </div>
    </v-parallax>
    <!-- <TheBanner v-else /> -->

    <BaseLayout>
      <PlaceSlide :places="places"></PlaceSlide>
      <rating-slide :places="popularPlaces"></rating-slide>
    </BaseLayout>
    <AboutCambodia />
    <BaseLayout>
      <local-slide :places="localPlaces"></local-slide>
      <trends-slide :citys="trendCitys"></trends-slide>
    </BaseLayout>
    <JoinUs />
    <div class="mb-5">
      <BaseLayout>
        <our-team />
      </BaseLayout>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      show: true,
      windowWidth: window.innerWidth,
      places: ['', '', '', '', '', ''],
      popularPlaces: ['', '', '', '', '', ''],
      localPlaces: [],
      trendCitys: ['', '', ''],
    }
  },
  methods: {
    //get all places
    getPlace() {
      this.$axios
        .get('place/all?item_per_page=200&select=saved')
        .then((res) => {
          // console.log(res.data.data.docs)
          this.places = res.data.data.docs
        })
    },
    //get popular place
    getPopular() {
      this.$axios
        .get(
          '/place/all?item_per_page=6&most_comment=true&select=story,averageRating,city'
        )
        .then((res) => {
          setTimeout(() => {
            this.popularPlaces = res.data.data.docs
          }, 3000)
        })
    },
    //get popular place
    getLocalPlace() {
      this.$axios.get('/city/all').then((res) => {
        this.localPlaces = res.data.data
      })
    },
    //get Trendind
    getTrending() {
      this.$axios.get('/trending/get/all').then((res) => {
        this.trendCitys = res.data.data.docs
      })
    },
    //responsive mobile
    handleResize() {
      if (window.innerWidth < 1281 && this.show == true) {
        this.show = false
      } else if (window.innerWidth >= 1281) {
        this.show = true
      }
    },
  },

  //get province and city place
  created() {
    this.getLocalPlace()
    this.getPlace()
    this.getPopular()
    this.getTrending()
  },
}
</script>
<style>
.v-parallax__content {
  padding: 0px !important;
}
</style>
