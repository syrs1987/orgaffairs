<template>
  <div>
  <div id="selType">
  <div id="selCityArea" class="sel">
    <Dropdown  trigger="click" >
      <Button type="primary">
        {{area}}
        <Icon type="ios-arrow-down"></Icon>
      </Button>
      <DropdownMenu slot="list" v-for="(items,index) in arealist" :key="index">
        <DropdownItem v-if="items.street.length==0"><span @click="setArea(items.area)">{{items.area}}</span></DropdownItem>
        <Dropdown trigger="click" placement="right-start" v-else>
          <DropdownItem>
            <span @click="setArea(items.area)">{{items.area}}</span>
            <Icon type="ios-arrow-forward"></Icon>
          </DropdownItem>
          <DropdownMenu slot="list">
            <DropdownItem v-for="(item,index) in items.street" :key="index"><span @click="setArea(item)">{{item}}</span></DropdownItem>
          </DropdownMenu>
        </Dropdown>
      </DropdownMenu>
    </Dropdown>
  </div>
  <div class="sel">
    <Dropdown trigger="click">
    <Button type="primary">
      {{hall}}
      <Icon type="ios-arrow-down"></Icon>
    </Button>
    <DropdownMenu slot="list">
      <DropdownItem v-for="(item,index) in halllist" :key="index"><span @click="sethall(item)">{{item}}</span></DropdownItem>
      </DropdownMenu>
  </Dropdown></div>
  <div  class="sel">
    <Dropdown trigger="click">
    <Button type="primary">
      {{business}}
      <Icon type="ios-arrow-down"></Icon>
    </Button>
    <DropdownMenu slot="list" >
      <DropdownItem v-for="(item,index) in businesslist" :key="index"><span @click="setBusi(item)">{{item}}</span></DropdownItem>
    </DropdownMenu>
  </Dropdown>
  </div>
  </div>
    <div style="height:20px"></div>
  <div id="itemListDiv">
    <ClassItem v-if="rcomData.length > 0" :title="'服务大厅'" :dataes="rcomData"></ClassItem>
  </div>
  </div>
</template>
<script>
  import Vue from 'vue'
  import iView from 'iview'
  import ClassItem from './../components/class-Item.vue'
  import 'iview/dist/styles/iview.css'    // 使用 CSS

  Vue.use(iView, {
    transfer: true,
    size: 'large'
  });
  export default {
    name: 'learingList',
    data () {
      return {
        area: "区域选择",
        arealist:[{"area":"新吴区","street":["旺庄","硕放","江溪","鸿山","新安","梅村"]},{"area":"滨湖区","street":["马山","蠡园","华庄","雪浪","太湖","和埒","荣巷","蠡湖","胡埭"]},{"area":"惠山区","street":[]}],
        hall: "大厅分类",
        halllist:["银行","政务","税务","社区","街道"],
        business: "业务分类",
        businesslist:["银行存款","纳税申报","税务登记","日常缴费","街道服务","投资理财"],
        rcomData: [{"id": 1, "traffic": "公交1、2、3路，地铁一号线扬名站", "name": "中铭慧业软件技术有限公司无锡分公司1123","addr":"无锡市扬名街道南湖大道855号1901室","ytime":"2018年08月01日 14:00—16:00","orderW":"综合服务"},
          {"id": 3, "traffic": "公交1、2、3路，地铁一号线扬名站", "name": "中铭慧业软件技术有限公司","addr":"无锡市扬名街道南湖大道855号1901室","ytime":"2018年08月01日 14:00—16:00","orderW":"综合服务"}
        ]
      }
    },
    methods:{
      setArea:function(areaName) {
        this.area = areaName
      },
      sethall:function(areaName) {
        this.hall = areaName
      },
      setBusi:function(areaName) {
        this.business = areaName
      }
    },
    components: {
      iView,
      ClassItem
    }
  }
</script>

<style lang="scss">

#selType {
  margin-top: 5px;
  margin-bottom: 10px;
  .ivu-dropdown{
    width: 100%;
  }
}
#itemListDiv .classItem{
  margin-top: 10px;
}
#selType .sel{
  width: 33%;
  float: left;
  margin-left: 1px;
  .ivu-btn{
    width: 100%;
  }
}

</style>
