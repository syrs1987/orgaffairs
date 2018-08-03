<template>
  <div>
  <loginHeader></loginHeader>
  <mapHeader></mapHeader>
    <a v-for="(item, index) in lineupData" :key="index">
      <div class="lineitem">
        <div class="otype">综合服务</div>
        <div class="info">
          <div class="des">窗口号:{{item.wno}}</div>
          <div class="des">当前办理:<span style="color: red">{{item.currentno}}</span>号</div>
          <div class="des">等候数: <span style="color: red">{{item.waitno}}</span>位</div>
        </div>
      </div>
    </a>
    <div class="footer">
      <mt-button type="primary" @click="appoint" class="detaibtn">立即预约</mt-button>
      <mt-button type="primary" @click="lineup"  class="detaibtn">刷新</mt-button>
    </div>
  </div>
</template>
<script>
import msgItem from './../components/msg-Item'
import loginHeader from './../components/header/login-head.vue'
import mapHeader from './../components/header/map-head.vue'
  export default {
    name: 'lineup',
    data() {
      return {
        selected: 'all',
        lineupData: [{"otype": "综合服务", "wno": "1,2,3,4","currentno":"2001","waitno":20},
          {"otype": "项目申报", "wno": "5,6,7,8","currentno":"3441","waitno":12}
        ]
      }
    },
    methods:{
    },
    components:{
      msgItem,
      loginHeader,
      mapHeader
    }
  }
</script>

<style lang="scss">
.lineitem{
  margin: 4px;
  border-radius: 5%;
  padding: 6px;
  background: #BFCFD7;
  color:#000;
  .otype{
    margin-top: 5px;
    height: 20px;
    font-size:24px;
    margin-bottom: 15px;
  }
  .des{
    margin-top: 5px;
    font-size:20px;
    letter-spacing:8px;
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
</style>
