<!--
 -  2019/1/14  lize
 -->
<template>

  <div class = "RadioTem">

    <div class = "Radio-test-questions-title">

      <!--<van-cell style = "font-size: 16px;" >{{data.subscript+'、'+data.title}}（最多选择{{data.max}}个）</van-cell>-->

      <p  style = "margin-bottom: 10px;padding: 10px 10px;border-bottom: 1px solid #ebedf0;font-size: 16px;">标题：{{data.title}}</p>

    </div>

    <div class = "Radio-test-questions-operation">

      <van-radio-group v-model="data.value[0].radio" class="demo-radio-group">

        <van-radio v-for="(item,index) in data.content" :name="item" :key = "index+1">{{item.title}}</van-radio>

      </van-radio-group>

    </div>

    <div class = "Remarks-div">

      <van-cell-group>

        <van-field

          v-model="data.remarks.value"

          type="textarea"

          label="入选理由"

          placeholder="请输入留言"

          rows="1"

          :error-message ="data.remarks.message"

          @blur = "RemarksOnBlur(data.remarks)"

          :autosize = "{maxHeight:200,minHeight:50}"

          :required = "data.remarks.force_explanation ? true : false "

        >

        </van-field>

      </van-cell-group>

    </div>

  </div>

</template>

<script>
    export default {
        props:['data','overallLnegth'],

        data () {
            return {}
        },
        mounted () {

        },
        methods: {

          //富文本失去焦点
          RemarksOnBlur(obj){

            obj.value.replace(/\s+/g,"");

            if(!obj.value){

              obj.message = "格式错误！";

              return

            }else{

              if(this.$fs.isChinese(obj.value)){

                obj.message = "格式错误！";

                return

              }else{

                obj.message = "";

                return

              }

            }

          },

        }

    }
</script>

<style scoped lang="scss">
  .RadioTem{

    background: #ffffff;

  }

  .van-cell{

    border-bottom: 1px solid #ebedf0;

  }
  .Radio-test-questions-operation{

    padding: 0 15px;

    .van-radio-group{

      .van-radio{

        margin-bottom: 10px;

        padding: 10px 0;

        border-bottom: 1px solid #ebedf0;

      }

    }

  }

  .van-radio{

    margin-bottom: 20px;

  }
  .Remarks-div{

    margin-top: 30px;

    padding: 0 10px;

  }
</style>
