<template>
    <div>
      <headTop></headTop>
      <baidumap></baidumap>
    </div>
</template>

<script>
  import baidumap from './../components/baidumap.vue'
  import headTop from '../components/header/map-head.vue'
    export default {
      name: "bmap",
      components:
      {
        baidumap,
        headTop
      }
  }
</script>

<style scoped>

</style>
