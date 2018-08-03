 <template>
  <div class="formItem">
    <headTop></headTop>
    <mt-field label="姓名" v-model="realname" :state="state" disableClear placeholder="姓名"></mt-field>
    <mt-field label="手机号" v-model="mobile" :state="state" disableClear placeholder="手机号"></mt-field>
    <mt-field label="身份证" v-model="cardno" :state="state" disableClear placeholder="身份证"></mt-field>
    <!--<mt-field label="业务类型" v-model="ordertype" :state="state" disableClear placeholder="业务类型" @focus.native.capture="actionSheet"></mt-field>-->
    <!--<mt-actionsheet-->
      <!--:actions="actions"-->
      <!--v-model="sheetVisible">-->
    <!--</mt-actionsheet>-->
    <mt-field label="预约时间" placeholder="" v-model="nowday" type="date" disableClear></mt-field>
    <!--<el-select-->
      <!--placeholder="请选择审批人"-->
      <!--value-key="name"-->
      <!--v-model="actions">-->
      <!--<el-option-->
        <!--v-for="item in actions"-->
        <!--:key="item.otId"-->
        <!--:label="item.oName"-->
        <!--:value="item">-->
      <!--</el-option>-->
    <!--</el-select>-->
    <div class="upLoadImg_Div">
      <div class="upimg_title">上传照片</div>
      <div> <imageupload></imageupload></div>
    </div>

    <div class="subBut" @click="orderSub">提交</div>
    <div class="subBut">取消</div>
    <div style="clear:both">
      <learingFooter></learingFooter>
    </div>

  </div>

</template>
<script>
  import {Cell,MessageBox,DatetimePicker,Actionsheet} from 'mint-ui'
  import headTop from '../components/header/map-head'
  import imageupload from '../components/image-html5-upload'
  import learingFooter from './../components/footer.vue'

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
        sheetVisible:false,
        actions:[{oName:"综合",otId:1},{oName:"公司",otId:2},{oName:"个人",otId:2}]
      }
    },
    methods:{
      orderSub:function () {
        alert(1);
      },
      actionSheet: function(){
        // 打开action sheet
        this.actions=[{oName:"综合",otId:1},{oName:"公司",otId:2},{oName:"个人",otId:2}]
        this.actions.forEach((v, i) => {
          this.actions.push({
            name: v.oName,
            method: this.setOtype(v.oName)
          });
        });
        this.sheetVisible = true;
      },
      setOtype: function(oName){
        console.info(oName);
        this.ordertype =  oName;
      }
    },
    components:{
      DatetimePicker,
      MessageBox,
      headTop,
      Cell,
      Actionsheet,
      imageupload,
      learingFooter
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
  .mint-cell-text{
    width: 20%;
  }
  .upLoadImg_Div{

    .upimg_title{
      padding: 5px;
    }
  }

</style>
