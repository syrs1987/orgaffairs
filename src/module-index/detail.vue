<template>

  <div class="learingIndexDetail">
    <loginHeader></loginHeader>
    <mapHeader></mapHeader>
    <!--<mt-header title="数据分析">-->
      <!--<router-link :to="{ go: '-1'}" slot="left">-->
        <!--<mt-button icon="back"></mt-button>-->
      <!--</router-link>-->
    <!--</mt-header>-->
    <div class="banner">
      <img src="../assets/banner.png" alt="">
      <span>{{compInfoData.name}}</span>
    </div>
    <div class="contentInfo">
      <!--简介-->
      <div class="fitPeop">
        <div class="tit">简介</div>
        <div>{{compInfoData.intro}}</div>
      </div>
      <!--地址-->
      <div class="fitPeop">
        <div class="tit">地址</div>
        <div>{{compInfoData.addr}}</div>
      </div>
      <!--营业时间-->
      <div class="fitPeop">
        <div class="tit">营业时间</div>
        <div>{{compInfoData.ytime}}</div>
      </div>
      <!--公共交通-->
      <div class="fitPeop">
        <div class="tit">公共交通</div>
        <div>{{compInfoData.traffice}}</div>
      </div>
      <!--服务窗口-->
      <div class="fitPeop">
        <div class="tit">服务窗口</div>
        <div>{{compInfoData.winfo}}</div>
      </div>
      <!--业务详情-->
      <div class="fitPeop">
        <div class="tit">业务详情</div>
        <div>{{compInfoData.business}}</div>
      </div>

    </div>
    <div class="footer">
      <mt-button type="primary" @click="appoint" class="detaibtn">立即预约</mt-button>
      <mt-button type="primary" @click="lineup"  class="detaibtn">排队状态</mt-button>
    </div>
  </div>
</template>
<script>
  import learingFooter from './../components/footer.vue'
  import IndexApi from '../api/learingInd.js'
  import cfg from './../utils/config'
  import Base from '../api/base'
  import loginHeader from './../components/header/login-head.vue'
  import mapHeader from './../components/header/map-head.vue'

  export default {
    name: 'learingIndexDetail',
    mixins: [Base],
    data() {
      return {
        imgBaseUrl: cfg.imgBaseUrl,
        compInfoData: {
          "id": 1,
          "intro": "简介内容",
          "traffice": "公共交通:公交1、2、3路，地铁一号线扬名站",
          "name": "中铭慧业软件技术有限公司",
          "addr": "无锡市扬名街道南湖大道855号1901室",
          "ytime": "2018年08月01日 14:00—16:00",
          "winfo": "1-10号 窗口 综合服务 11-15号窗口 项目申报16-20号窗口  税务登记",
          "business": "综合服务：办理个人存款、取款、开户、注销等个人基本业务 项目申报：办理项目申报、审核、查询等业务 税务登记：办理税务登记、查询、修改等业务"
        }
      }
    },
    methods: {
      // 初始化数据
      init: function () {
        IndexApi.courses({id: this.$route.params.classId}, (ret, err) => {
          if (err) {
            console.log(err)
          } else {
          }
        })
      },
      // 课程大纲
      getCourseItem: function (obj) {
        IndexApi.coursesutline({id: obj}, (ret, err) => {
          if (err) {
            console.log(err)
          } else {
          }
        })
      },
      //返回上一页
      goBack: function () {
        this.$router.go(-1)
      },
      appoint:function () {
        this.$router.push({path:'/order/'})
      },
      lineup:function () {
        this.$router.push({path:'/lineup/'})
      }
    },
    mounted: function () {
      this.init()
    },
    components: {
      learingFooter,
      loginHeader,
      mapHeader
    }
  }
</script>

<style lang="scss">
  @import "../assets/baseScss";
.learingIndexDetail{
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  overflow: auto;
  text-align: center;
  .banner{
    position: relative;
    z-index: 99;
    color:$cl1;
    font-size: 24px;
    span{
      font-weight: bold;
      position: absolute;
      top:50%;
      left:50%;
      transform:translate(-50%, -50%);
    }
  }
  .top{
    background: $cl1;
    position: relative;
    line-height: 40px;
    color:$cl7;
    font-size: 14px;
    span:before{font-size: 15px;}
    span:nth-child(1){
      position: absolute;
      top:10px;
      left:10px;
    }
    span:nth-child(2){
      position: absolute;
      top:10px;
      right:15px;
    }
  }
  .contentInfo{
    min-height: 100%;
    padding:10px;
    margin-bottom: 60px;
    .desInfo{
      background: $cl1;
      font-size: 12px;
      .des{
        color: $cl6;
        line-height: 28px;
        text-align: left;
        padding:10px;
        border-bottom: solid 1px $cl5;
      }
      ul{
        color:$cl3;
        width: 100%;
        display: flex;
        padding:5px 0px;
        li{
          flex: 1;
          text-align: center;
          border-right: solid 1px $cl5;
          em{
            color:$cl15;
          }
        }
        li:last-child{
          border:none;
        }
      }
    }
  }
  .teachInfo{
    display: flex;
    padding:10px 0;
    background: $cl1;
    margin: 10px 0;
    .teach{
      flex: 1;
      text-align: center;
      img{
        width: 50px;
        border-right: 50px;
        display: inline-block;
      }
    }
    .info{
      flex: 3;
      text-align: left;
      color:$cl6;
      font-size: 14px;
      p{
        height: 25px;
        line-height: 25px;
        overflow: hidden;
      }
      .name{
        color: $cl3;
        font-size: 16px;
      }
    }
    .goAbout{
      flex: 1;
      color:$cl9;
      i{
        position: relative;
        top:20px;
      }
    }
  }
  .fitPeop{
    padding:10px;
    background: $cl1;
    margin: 10px 0;
    font-size: 12px;
    line-height: 28px;
    color:$cl6;
    text-align: left;
    .tit{
      font-size: 14px;
      color: $cl3;
    }
  }

  .footer {
    width: 100%;
    position:fixed; bottom:0;
    height: 50px;
    .detaibtn{
      width: 40%;
      float: left;
      margin-left: 7%;
    }
  }
}
</style>
