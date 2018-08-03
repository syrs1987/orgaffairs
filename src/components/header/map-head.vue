<template>
  <div>
    <mt-header title="中铭慧业超级大厅">
      <router-link to="/" slot="left">
        <mt-button icon="back">当前服务厅</mt-button>
      </router-link>
      <mt-button slot="right" class="spMap"><router-link to="/baidumap" style="color:white">地图</router-link></mt-button>
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

.spMap{
  font-size: 16px;
  color: white;
}
</style>
