<template>
    <div class="indexHeader">
      <div class="search" @click="goSeach" ><i class="icon-search" ></i> <input type="text" @blur="" @focus="" :style="{width: seachWt}" v-model="searchName" placeholder="办事在线"></div>
      <mt-swipe :auto="3000">
        <mt-swipe-item v-for="(item, index) in bannerDat" :key="index"><img :src="imgBaseUrl + item.image_url" width="100%" alt=""></mt-swipe-item>
      </mt-swipe>
    </div>
</template>

<script>
  import IndexApi from '../api/learingInd.js'
  import cfg from './../utils/config'
  import { Header } from 'mint-ui'
  export default {
    name: 'indexHeader',
    data () {
      return {
        bannerDat: [],
        searchName: '',
        seachWt: '',
        imgBaseUrl: cfg.imgBaseUrl,
      }
    },
    methods: {
      init:function (){
        IndexApi.banner((ret, err) => {
          if (err) {
            console.log('数据获取失败！')
          }else{
            this.bannerDat = ret.data
          }
        })
      },
      // 首页搜索
      goSeach: function() {
        this.$router.push({path:'/search/'})
      },
      // 搜索处理
      onblurEvent: function() {
        if (this.searchName === '') {
          this.seachWt = '65px'
        } else {
          this.seachWt = '90%'
        }
      },
      focusEvent: function() {
          this.seachWt = '90%'
      }
    },
    mounted:function(){
      this.init()
    },
    components:{
      Header
    }
  }
</script>
<style lang="scss">
  @import "../assets/baseScss";
  .spMap{
    font-size: 16px;
    color: white;
  }
  .chouse{
    font-color:#eee;
  }
  .addrspan{
    font-size: 15px;
    margin-left: 6px;
  }
  .sddrimg{
    width: 17px;
    height: 17px;
  }
  .login_link
  {
    color: #fff;
  }
  .indexHeader{
    height: 200px;
    position: relative;
  }
  .indexHeader{
    .search{
      position: absolute;
      z-index: 99;
      width: 90%;
      left: 5%;
      top:10px;
      background: rgba(255, 255, 255, 0.9);
      color:$cl4;
      line-height: 35px;
      input{
        height: 35px;
        width: 65px;
        line-height: 35px;
        background: transparent;
        border: none;
        font-size: 16px;
        padding:0 1px;
      }
      input:focus{
        outline:medium;
        width: 85%;
      }
      i:before{
        position: relative;
        font-size: 16px;
        top:1px;
        left: 3px;
      }
    }
  }
</style>
