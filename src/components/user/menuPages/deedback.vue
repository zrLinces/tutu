<template>
  <div class="feedback">
    <Rheader name="反馈建议"/>
    <div class="feedback-top">
      <div class="back-t">
        <textarea class="sugge" cols="30" rows="10"></textarea>
      </div>
      <div class="sug" @click="sug"><p>提交反馈</p></div>
    </div>
  </div>
</template>
<script>
import Rheader from "./userHeader.vue";
export default {
  methods:{
    sug(){
      console.log("提交建议")
    }
  },
  components: {
    Rheader
  }
};
</script>
<style lang="scss">
.feedback {
  height: 100%;
}
.feedback-top {
  height: 100%;
  background: #f3f4f6;
}
.back-t{
  padding: 10px;
}
.sugge{
  width: 100%;
  outline: none;
  border: 0;
  font-size: 16px;
}
.sug{
  padding: 10px;
  p{
    width: 100%;
    background: #4a4c5b;
    height: 40px;
    color: #fff;
    line-height: 40px;
    text-align: center;
    font-size: 18px;
  }
}
</style>
