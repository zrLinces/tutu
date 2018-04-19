<template>
    <div class="id">
        <div class="id-top">
            <i class="iconfont icon-zuojiantou" @click="back"></i>
            <p>实名认证</p>
            <div></div>
        </div>
        <div class="id-content">
            <div class="id-number">
                <span>身份证号</span>
                <span class="reg" v-show="reg1">请填写正确的身份证号码</span>
                <input type="text" maxlength="18" placeholder="请填写18位身份证号" v-model="idnumber">
            </div>  
            <div class="name">
                <p>真实姓名</p>
                <input type="text" placeholder="请填写身份证姓名" v-model="name">
            </div>
            <div class="sumbit" v-show="bool"><p>提交审核</p></div>
            <div class="sumbit-to" v-show="boll" @click="sumbit"><p>提交审核</p></div>
        </div>
    </div>
</template>
<script>
export default {
  data() {
    return {
      bool: true,
      boll: false,
      idnumber: "",
      name: "",
      id: false,
      xm: false,
      bolen: false,
      reg1: false
    };
  },
  watch: {
    idnumber() {
      if (this.idnumber.length == 18) {
        if(/^[1-9]\d{5}(18|19|([23]\d))\d{2}((0[1-9])|(10|11|12))(([0-2][1-9])|10|20|30|31)\d{3}[0-9Xx]$/.test(this.idnumber)){
          this.id = true;
        }else{
          this.reg1 = true;
        }
      } else {
        this.reg1 = false;
        this.id = false;
      }
      this.show();
    },
    name() {
      if (/[\u4e00-\u9fa5]{2,}/.test(this.name)) {
        this.xm = true;
      } else {
        this.xm = false;
      }
      this.show();
    }
  },
  methods: {
    back() {
      this.$router.replace({ path: "/user/setting" });
    },
    show() {
      if (this.id && this.xm) {
        this.bool = false;
        this.boll = true;
      } else {
        this.bool = true;
        this.boll = false;
      }
    },
    sumbit(){
        console.log("提交审核")
    }
  }
};
</script>
<style lang="scss">
.id {
  height: 100%;
}
.id-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 6%;
  font-size: 18px;
  padding: 0 15px;
  color: #353535;
  box-shadow: 0px 2px 3px rgba(0, 0, 0, 0.1);
  margin-bottom: 2px;
  .icon-zuojiantou {
    font-size: 18px;
  }
}
@mixin id {
  padding: 10px;
  input {
    margin-top: 10px;
    height: 20px;
    width: 95%;
    outline: none;
    border: 1px solid #e6e6e6;
    padding: 10px;
  }
}
.id-number {
  @include id;
}
.name {
  @include id;
}
@mixin sumbit {
  padding: 10px;
  p {
    height: 45px;
    line-height: 45px;
    text-align: center;
    color: #fff;
  }
}
.sumbit {
  @include sumbit;
  p {
    background: #cccccc;
  }
}
.sumbit-to {
  @include sumbit;
  p {
    background: #4a4c5b;
  }
}
.reg{
  color: red;
  margin-left: 20px;
}
</style>
