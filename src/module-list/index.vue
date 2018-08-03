<template>
  <div>
  <Dropdown>
    <a href="javascript:void(0)">
      北京小吃
      <Icon type="ios-arrow-down"></Icon>
    </a>
    <DropdownMenu slot="list">
      <DropdownItem>驴打滚</DropdownItem>
      <DropdownItem>炸酱面</DropdownItem>
      <DropdownItem>豆汁儿</DropdownItem>
      <Dropdown placement="right-start">
        <DropdownItem>
          北京烤鸭
          <Icon type="ios-arrow-forward"></Icon>
        </DropdownItem>
        <DropdownMenu slot="list">
          <DropdownItem>挂炉烤鸭</DropdownItem>
          <DropdownItem>焖炉烤鸭</DropdownItem>
        </DropdownMenu>
      </Dropdown>
      <DropdownItem>冰糖葫芦</DropdownItem>
    </DropdownMenu>
  </Dropdown>
  </div>
</template>
<script>
  import {Dropdown} from 'iview'
  import 'iview/dist/styles/iview.css'

  export default {
    name: 'typeList',
    data() {
      return {
        showArea:false,
        items: [
          {
            name: '家用电器',
            isSubShow: false,
            subItems: [
              {
                name: '笔记本电脑'
              },
              {
                name: '台式电脑'
              },
              {
                name: '电视机'
              }
            ]
          },
          {
            name: '服装',
            isSubShow: false,
            subItems: [
              {
                name: '男士服装'
              },
              {
                name: '女士服装'
              },
              {
                name: '青年服装'
              }
            ]
          }
        ]
      }
    },
    methods: {
      showToggle: function (item) {
        item.isSubShow = !item.isSubShow
      },
      choArea: function () {
        this.showArea=true;
      }
    },
    components:{
      Dropdown
    }
  }
</script>

<style lang="scss">

</style>
