<template>
  <div id="container" ref="map">
  
  </div>
</template>

<script>
export default {
  methods: {
    createMap() {
      var map = new AMap.Map('container', {
        resizeEnable: true,
        zoom: 10
      })
      this.$store.dispatch('getCurrentPosition', map)
    }
  },
  mounted() {
    this.createMap()
  }
}
</script>
  <style>
#container {
  height: 100%;
}
</style>
