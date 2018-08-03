<template>
  <div>
  <loginHeader titleName="首页"></loginHeader>
  <div class="learingIndex">
    <mt-tab-container v-model="selected" swipeable="swipeable">
      <mt-tab-container-item id="index">
        <LearingHeader></LearingHeader>
        <ClassItem v-if="rcomData.length > 0" :title="'服务大厅'" :dataes="rcomData"></ClassItem>
        <!--<ClassItem v-if="courseData.length > 0" :title="'数据分析'" :labs="'true'" :dataes="courseData"></ClassItem>-->
      </mt-tab-container-item>
      <mt-tab-container-item id="list">
        <listModular></listModular>
      </mt-tab-container-item>
      <mt-tab-container-item id="order">
        <listModular></listModular>
      </mt-tab-container-item>
      <mt-tab-container-item id="course">
        <courseModular></courseModular>
      </mt-tab-container-item>
      <mt-tab-container-item id="my">
        <myModular></myModular>
      </mt-tab-container-item>
    </mt-tab-container>

    <div class="learingFooter">
      <mt-tabbar v-model="selected" :fixed="true">
        <mt-tab-item id="index" >
          <i class="icon icon-ind"></i>
          首页
        </mt-tab-item>
        <mt-tab-item id="list" >
          <i class="icon icon-class"></i>
          分类
        </mt-tab-item>
        <mt-tab-item id="order" >
          <i class="icon icon-order"></i>
          预约
        </mt-tab-item>
        <mt-tab-item id="course">
          <i class="icon icon-notice"></i>
          消息
        </mt-tab-item>
        <mt-tab-item id="my">
          <i class="icon icon-my"></i>
          我的
        </mt-tab-item>
      </mt-tabbar>
    </div>
  </div>
  </div>
</template>
<script>
  import httpCt from '../api/httpClient'
  import LearingHeader from './../components/index-header.vue'
  import ClassItem from './../components/class-Item.vue'
  import listModular from './../module-list/index.vue'
  import courseModular from './../module-course/index.vue'
  import myModular from './../module-my/index.vue'
  import learingFooter from './../components/footer.vue'
  import IndexApi from '../api/learingInd.js'
  import cfg from './../utils/config'
  import loginHeader from './../components/header/login-head.vue'
  export default {
    name: 'learingIndex',
    data () {
      return {
        rcomData: [{"id": 1, "traffic": "公交1、2、3路，地铁一号线扬名站", "name": "中铭慧业软件技术有限公司无锡分公司1123","addr":"无锡市扬名街道南湖大道855号1901室","ytime":"2018年08月01日 14:00—16:00","orderW":"综合服务"},
          {"id": 3, "traffic": "公交1、2、3路，地铁一号线扬名站", "name": "中铭慧业软件技术有限公司","addr":"无锡市扬名街道南湖大道855号1901室","ytime":"2018年08月01日 14:00—16:00","orderW":"综合服务"}
        ],       // 推荐课程
        courseData:  [{"id": 1, "status": "未办理", "name": "中铭慧业软件技术有限公司无锡分公司1123","addr":"无锡市扬名街道南湖大道855号1901室","ytime":"2018年08月01日 14:00—16:00","orderW":"综合服务"},
          {"id": 3, "status": "已办理", "name": "中铭慧业软件技术有限公司","addr":"无锡市扬名街道南湖大道855号1901室","ytime":"2018年08月01日 14:00—16:00","orderW":"综合服务"}
        ],
        swipeable: 'false',
        selected: 'index',
        imgBaseUrl:cfg.imgBaseUrl,
        param:{}
      }
    },
    methods:{
      init: function() {
        let sel = this.$route.path
        if (sel.slice(1)){
          this.selected = sel.slice(1)
        }
        // 精品推荐
        this.getCourseItem('rcom')
        // 全部分类
        this.getCourseItem()
      },
      getCourseItem: function(obj){
        if(obj){
          this.param.rcom = true
          this.param.page = 10
        }else{
          this.param.rcom = ''
          this.param.page = 20
        }
        IndexApi.coursesItem(this.param,(ret, err) => {

          if (err) {
            console.log(err)
          }else{
            if(obj){
            }else{
              this.courseData = ret.data
            }
          }
        })
      }
    },
    watch:{
      selected(val, oldVal){
        this.$router.push(val)
      }
    },
    mounted:function(){
      this.init()
    },
    components: {
      LearingHeader,
      ClassItem,
      listModular,
      courseModular,
      myModular,
      learingFooter,
      loginHeader
    }
  }
</script>

<style lang="scss">
  @import "../assets/baseScss";
.learingIndex{
  text-align: center;
}
.learingFooter{
  color:$cl7;
  margin-top: 51px;
.icon{
  display: block;
  font-size: 22px;
  margin-bottom: 3px;
}
}
</style>
