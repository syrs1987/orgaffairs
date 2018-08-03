<template>
  <div>
    <baidu-map class="map" :center="center" :zoom="zoom" :scroll-wheel-zoom="true"
               :style="styleMap" @ready="handler" @click="mapclick">
      <!--<bm-geolocation anchor="BMAP_ANCHOR_BOTTOM_RIGHT" :showAddressBar="false" :autoLocation="true"-->
                      <!--:locationIcon="{url: require('./../assets/addr.png'), size: {width: 18, height: 18}}"-->
                      <!--&gt;-->
      <!--</bm-geolocation>-->
      <!--&lt;!&ndash; 自定义定位图标覆盖物 &ndash;&gt;-->
      <bm-marker :position="autoLocationPoint" :clicking="true"
                 :icon="{url:require('./../assets/addr_w.png'), size: {width: 20, height: 22}}">
      </bm-marker>
      <!--<bm-local-search :keyword="keyword" :auto-viewport="true" style="width:0px;height:0px;overflow: hidden;"></bm-local-search>-->
    </baidu-map>

  </div>
</template>

<script>
  import Vue from 'vue'
  import BaiduMap from 'vue-baidu-map'

  Vue.use(BaiduMap, {
    // ak 是在百度地图开发者平台申请的密钥 详见 http://lbsyun.baidu.com/apiconsole/key */
    ak: 'VbxmYezc8jmkvH6gGNfktwlMCHk9o1nM'
  })
  export default {
    conponents:{
      BaiduMap
    },
    data () {
      return {
        // 省略一部分
        center: {lng: '112.37884', lat: ' 34.646767'},
        autoLocationPoint: {lng: '112.37', lat: ' 34.64'},
        zoom:15,
        initLocation: true,
        fullHeight: document.body.clientHeight,
        fullWidth: document.body.clientWidth,
        styleMap:{
          height:'',
          width:''
        },
        keyword:''
      }
    },
    methods: {
      mapclick(e){
        this.center.lng = e.point.lng
        this.center.lat = e.point.lat
        this.autoLocationPoint.lng = e.point.lng
        this.autoLocationPoint.lat = e.point.lat
      },
      handler () {
       // navigator.geolocation.getCurrentPosition(this.translatePoint, this.geo_error);

        // 下面注释是百度地图API官方实现方法，因为我使用自定义图标覆盖物，所以没有使用这种方法！
        // 如使用以下这种方法，那么我Template里所写的自定义定位图标代码是不需要的
        // var geolocation = new BMap.Geolocation();
        // geolocation.getCurrentPosition(function(r){
        // if(this.getStatus() == BMAP_STATUS_SUCCESS){
        //   var mk = new BMap.Marker(r.point);
        //   map.addOverlay(mk);
        //   map.panTo(r.point);
        //   alert('您的位置：'+r.point.lng+','+r.point.lat);
        // }
        // else {
        //   alert('failed'+this.getStatus());
        // }
        // },{enableHighAccuracy: true})
      }
    },
    mounted () {
      // height:`${document.documentElement.clientHeight}`,
      //   width:`${document.documentElement.clientWidth}`
      this.styleMap.height=document.documentElement.clientHeight+'px';
    }
  }
</script>
<style scoped>
  /* 地图容器必须设置宽和高属性 */


</style>
