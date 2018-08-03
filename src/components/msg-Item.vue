<template>
  <div class="orderItem">
    <div class="content"  >
      <span v-for="(item, index) in orderData" :key="index" :href="'#/detail/'+ item.id">
        <div class="item">
          <div class="info" @click="toDetail(item.id)">
            <div class="tit">{{item.name}}</div><br/>
            <div class="des">地址:{{item.addr}}</div>
            <div class="des">预约时间:{{item.ytime}}</div>
            <div class="des">预约窗口:{{item.orderW}}</div>
          </div>
          <div class="rinfo">
            <div v-if="item.status=='未办理'" class="notext">{{item.status}}</div>
            <div v-if="item.status=='已办理'" class="yestext">{{item.status}}</div>
            <div><img class="map" src="../assets/addr_w.png"></div>
            <div>
              <vue-qr :bgSrc='src' :logoSrc="src2" :text="'http://172.21.24.83:8080/#/detail/'+item.id" :size="200"></vue-qr>
            </div>
          </div>
        </div>
      </span>
    </div>
  </div>
</template>
<script>
  import VueQr from 'vue-qr'
  export default {
    name: 'page-navbar',
    props:["orderData"],
    methods:{
      toDetail:function (id) {
        this.$router.push({path:'/detail/'+id});
      }
    },
    components:{
      VueQr
    }
  }
</script>

<style lang="scss">
  @import "../assets/baseScss.scss";
  .orderItem{
    padding:2px;text-align: left;margin-top: 2px;
    .title{
      text-align: left;font-size: 18px;padding: 5px 0;color: $cl0;position: relative;margin: 5px 0;
      i:before{font-size: 15px;color:$cl0;margin-right: 3px;}
      .labs{
        position: absolute;right: 10px;font-size: 12px;color: $cl7;top:8px;
      }
    }
    .content{
      .item{
        display: flex;border: #1cb0ee solid 2px; border-radius: 10px;padding: 3px;
        background-color: white;margin-top: 7px;
        .info{
          width: 80%;
          .tit{font-size: 18px; color:$cl2;height: 20px;  font-weight:bolder}
          .des{font-size: 16px; color:$cl6;height: 20px;overflow: hidden; margin: 5px 0;}
          .rank{
            font-size: 14px; color:$cl6; height: 20px;overflow: hidden;
            i{color:$cl9;}
            em{color:$cl15;}
          }
        }
        .rinfo{
          width:20%;
          text-align: center;
          .map{
            height: 25px;
            width: 25px;
          }
          div{
            margin-top: 5px;
          }
          .notext{
            color:red;
            font-size:16px;
            font-weight: bolder;
          }
          .yestext{
            color:deepskyblue;
            font-size:16px;
            font-weight: bolder;
          }
        }
      }
      .loading{
        text-align: center;
      }
      .loadNone{
        font-size: 12px;color:#999;text-align: center;
      }
    }
  }
</style>

