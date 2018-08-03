<template>
  <div class="headlogin">
  <mt-header :title="titleName">
    <mt-button icon="addr"  slot="left" @click="changPro"><img class="sddrimg" src="./../../assets/addr.png"/><span class="addrspan">{{cityName}}</span></mt-button>
    <mt-button slot="right">
      <svg class="user_avatar" v-if="false">
        <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#user"></use>
      </svg>
      <span v-else>
        <router-link to="login" class="login_link">登录</router-link>|<router-link class="login_link" to="register">注册</router-link></span>
    </mt-button>
  </mt-header>
    <mt-popup
      v-model="popupVisible"
      position="right"
      modal=false>
      <mt-index-list :show-indicator="false">
        <mt-index-section v-for="Zm in cityZm" :index="Zm">
          <mt-button  v-for="item in cityList[Zm]" :title="item.name" @click="setcity(item.name)">{{item.name}}</mt-button>
        </mt-index-section>
      </mt-index-list>
    </mt-popup>
  </div>
</template>

<script>
  import { Header,Popup,Button   } from 'mint-ui'
    export default {
      name: "login-head",
      props:["titleName"],
      data () {
        return {
          popupVisible:false,
          cityZm:[],
          cityList: [],
          cityName:"无锡"
        }
      },
      components:{
        Header,
        Popup,
        Button
      },
      methods:{
        changPro () {
        this.popupVisible=true;
        },
        setcity (cname) {
          this.cityName = cname;
          this.popupVisible = false;
        }
      },
      created:function() {
        var citydata = require("../../assets/json/china-city-data.json");
        this.cityList = citydata;

        for(var tmp in citydata) {
          this.cityZm.push(tmp);
        }
      }
    }
</script>


<style lang="scss">
  .headlogin{
    .mint-popup{
      width: 100%;
    }
  }
  .mint-indexlist-content{
    -webkit-overflow-scrolling: touch;
    overflow-scrolling: touch;
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
</style>
