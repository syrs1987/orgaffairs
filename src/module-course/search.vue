<template>
  <div class="courseSearch">
    <mt-search v-model="searchValue" placeholder="请输入搜索内容"></mt-search>
    <div class="searchBox">
      <div class="searchHot" v-if="searchResults ===  ''">
        <div class="title">热门搜索</div>
        <div class="labs">
          <li v-for="(item, index) in hotSearchItemData" :key="index" @click="searchHotCk(item.keyword)">{{item.keyword}}</li>
        </div>
      </div>
      <div class="searchResult" v-if="searchResults != ''">
        <div class="title">搜索结果</div>
        <div class="searchResultCont">
          <!--<span v-if="seachResultData.length == 0" style="color:#f00;line-height: 50px;">搜索结果为空！</span>-->
          <ClassItem :dataes="seachResultData" :isLoadMores="true" :loading="loading" @getloadMore="loadMore"></ClassItem>
        </div>
      </div>
    </div>
    <learingFooter></learingFooter>
  </div>
</template>
<script>
  import ClassItem from './../components/class-Item.vue'
  import learingFooter from './../components/footer.vue'
  import IndexApi from '../api/learingInd.js'
  import cfg from './../utils/config'

  export default {
    name: 'courseSearch',
    data () {
      return {
        imgBaseUrl:cfg.imgBaseUrl,
        searchValue: '',
        searchResults: '',
        hotSearchItemData: '',
        seachResultData: [],
        subParams: {},
        loading:false,
        noData:false
      }
    },
    methods:{
      init: function() {
        if (this.$route.params.searchName){
          this.subParams.searchValue = this.$route.params.searchName
          this.searchHotCk()
        } else if (!this.searchResults) {
            this.getSearchItem()
        }
      },
      // 获取热搜词列表
      getSearchItem: function(){
        IndexApi.seachItem((ret, err) => {
          if (err) {
            console.log(err)
          }else{
            this.hotSearchItemData = ret.data
          }
        })
      },
      //直接点击分类搜索
      searchHotCk: function(obj){
        this.searchValue = obj
        this.searchResults = obj
        this.subParams.currentPage = 1
        this.subParams.keyword = this.searchValue
        IndexApi.searchResults(this.subParams, (ret, err) => {
          if (err) {
            console.log(err)
          }else{
            this.seachResultData = ret.data
          }
        })
      },
      //加载更多
      loadMore:function(){
        if(this.noData){
          return false
        }
        this.loading = true
        this.subParams.currentPage++
        IndexApi.searchResults(this.subParams, (ret, err) => {
          if (err) {
            console.log('获取数据失败！')
          }else{
            if(ret.data.length == 0){
              this.noData = true
              this.loading = false
              return false
            }else{
              this.loading = false
              this.seachResultData = this.seachResultData.concat(ret.data)
            }
          }
        })
      }
    },
    watch: {
      searchValue(newval, oldval){
        console.log(newval)
        if(newval == ''){
          this.getSearchItem()
        }else{
          this.searchHotCk(newval)
        }
      }
    },
    mounted:function(){
      this.init()
    },
    components: {
      ClassItem,
      learingFooter
    }
  }
</script>

<style lang="scss">
  @import "../assets/baseScss";
  .courseSearch{
    .searchBox{
      padding:15px;
      .title{
        line-height: 40px;
        color:$cl9;
        font-size: 14px;
        border-bottom: solid 1px $cl5;
      }
      .searchHot{
        .labs{
          display: flex;
          flex-wrap:wrap;
          li{
            background:$cl5;
            color:$cl3;
            padding:3px 10px;
            margin: 10px 10px 0px 0px;
          }
        }
      }
      .searchResultCont{

      }
    }
  }
</style>
