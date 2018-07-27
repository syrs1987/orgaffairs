<template>
  <div>
  <mt-header title="预约办事">
    <mt-button icon="addr"  slot="left" ><img class="sddrimg" src="./../../assets/addr.png"/><span class="addrspan">无锡</span></mt-button>
    <mt-button slot="right">
      <svg class="user_avatar" v-if="userInfo">
        <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#user"></use>
      </svg>
      <span v-else>
        <router-link to="login" class="login_link">登录</router-link>|<router-link class="login_link" to="register">注册</router-link></span>
    </mt-button>
  </mt-header>
    <mt-header title="中铭慧业超级大厅">
      <router-link to="/" slot="left">
        <mt-button icon="back">当前服务厅</mt-button>
      </router-link>
      <mt-button slot="right" class="spMap"><span >地图</span></mt-button>
    </mt-header>
  </div>
</template>
<script>
  import { Header } from 'mint-ui'
    export default {
    	data(){
            return{

            }
        },
      components:{
        Header
      }
    }
</script>

<style lang="scss">
  .mint-header{
    background-color: #26a2ff;
    color: #fff;
  }
.spMap{
  font-size: 16px;
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
</style>
