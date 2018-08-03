<template>
  <div class="page-navbar">
    <!-- navbar -->
    <mt-navbar class="page-part" v-model="selected">
      <mt-tab-item id="all">全部</mt-tab-item>
      <mt-tab-item id="no">未办理</mt-tab-item>
      <mt-tab-item id="yes">已办理</mt-tab-item>
    </mt-navbar>
    <!-- tabcontainer -->
    <mt-tab-container v-model="selected">
      <mt-tab-container-item id="all">
        <msgItem :orderData="allData"></msgItem>
      </mt-tab-container-item>
      <mt-tab-container-item id="no">
        <msgItem :orderData="noData"></msgItem>
      </mt-tab-container-item>
      <mt-tab-container-item id="yes">
        <msgItem :orderData="yesData"></msgItem>
      </mt-tab-container-item>
    </mt-tab-container>
    <msgItem></msgItem>
  </div>
</template>
<script>
import msgItem from './../components/msg-Item'
  export default {
    name: 'page-navbar',
    data() {
      return {
        selected: 'all',
        allData: [{"id": 1, "status": "未办理", "name": "中铭慧业软件技术有限公司无锡分公司1123","addr":"无锡市扬名街道南湖大道855号1901室","ytime":"2018年08月01日 14:00—16:00","orderW":"综合服务"},
          {"id": 3, "status": "已办理", "name": "中铭慧业软件技术有限公司","addr":"无锡市扬名街道南湖大道855号1901室","ytime":"2018年08月01日 14:00—16:00","orderW":"综合服务"}
        ],
        noData: [{"id": 1, "status": "未办理", "name": "中铭慧业软件技术有限公司无锡分公司1123","addr":"无锡市扬名街道南湖大道855号1901室","ytime":"2018年08月01日 14:00—16:00","orderW":"综合服务"}
        ],
        yesData: [{"id": 3, "status": "已办理", "name": "中铭慧业软件技术有限公司","addr":"无锡市扬名街道南湖大道855号1901室","ytime":"2018年08月01日 14:00—16:00","orderW":"综合服务"}
        ]
      }
    },
    methods:{
    },
    components:{
      msgItem
    }
  }
</script>

<style lang="scss">
.page-part{
  font-size: 15px;
}
</style>
