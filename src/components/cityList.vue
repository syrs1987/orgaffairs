<template>
  <div>
    <mt-header title="天津" class='fs1-2' fixed>
      <mt-button slot="left"><mt-button icon="back"></mt-button></mt-button>
      <mt-button slot="right" class='fs0-8'>切换城市</mt-button>
    </mt-header>

    <div class="mgtop50 padlr10 bgfff padbot10">
      <input class="cityinput" placeholder="输入商务楼，学校，地址"></input>
      <div class="submit bgcol ih40">提交</div>
    </div>

    <div>
      <div class='contenttop fs0-8 padlr10'>搜索历史</div>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'citylist',
    data () {
      return {

      }
    },
    component:{
      //注册组件

    },
    mounted:function(){
      //生命周期
    },
    computed:{
      //计算属性

    },
    methods:{
      //函数
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .cityinput{
    width:100%;
    height:40px;
    margin:10px 0px;
    outline:0px;
    padding:0px 5px;
    box-sizing:border-box;
  }
  .submit{
    text-align:center;
    color:white;
    border-radius:3px;
  }
  .fs0-8{
    font-size:0.8rem !important;
  }
  .contenttop{
    border-top:2px solid #E4E4E4;
    border-bottom:2px solid #E4E4E4;
  }
</style>
