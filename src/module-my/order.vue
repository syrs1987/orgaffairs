<template>
  <div class="formItem">
    <headTop></headTop>
    <mt-field label="" v-model="realname" :state="state" disableClear placeholder="姓名"></mt-field>
    <mt-field label="" v-model="mobile" :state="state" disableClear placeholder="手机号"></mt-field>
    <mt-field label="" v-model="cardno" :state="state" disableClear placeholder="身份证"></mt-field>
    <mt-field label="" v-model="ordertype" :state="state" disableClear placeholder="业务类型"></mt-field>
    <mt-field label="预约时间" placeholder="" v-model="nowday" type="date" disableClear></mt-field>
    <mt-cell
      title="业务类型"
      to="ordertypeselect"
      is-link
      value="带链接">
    </mt-cell>

    <mt-select label="" v-model="ordertype" :state="state" disableClear placeholder="业务类型">
      <mt-option >
        123
      </mt-option>
    </mt-select>
  <div class="subBut" @click="orderSub">提交</div>
    <div class="subBut">取消</div>
  </div>
</template>
<script>
  import {MessageBox,DatetimePicker } from 'mint-ui'
  import headTop from '../components/header/head'

  export default {
    name: 'order',
    data () {
      return {
        dateTime: '',
        nowday: new Date(),
        ordertype:'1',
        cardno:'1',
        realname:'1',
        mobile:'1',
        state:'success',
        drifStatusOptions:[{"label":"1","label":"asd",}]
      }
    },
    methods:{
      orderSub:function () {
        alert(1);
      }
    },
    components:{
      DatetimePicker,
      MessageBox,
      headTop
    }
  }
</script>


<style lang="scss">
  @import "../assets/baseScss";
  .subBut{
    background: $cl0;
    color:$cl1;
    text-align: center;
    line-height: 40px;
    margin: 20px 0;
    width: 40%;
    margin-left: 7%;
    float: left;
    border-radius:7px;
  }
</style>
