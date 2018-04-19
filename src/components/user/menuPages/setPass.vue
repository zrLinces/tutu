<template>
  <div class="setPass">
    <div class="set-top">
        <i class="iconfont icon-zuojiantou" @click="back"></i>
        <p>设置登录密码</p>
        <div></div>
    </div>
    <div class="set-content">
        <div class="set-title">密码由8-16位英文字母、数字或字符组成</div>
        <div class="set-pass">
          <span>设置密码</span>
          <input type="password" placeholder="请输入8-16位密码" maxlength="16" v-model="word">
        </div>
        <div class="in" v-show="before"><p>确定</p></div>
        <div class="in-to" v-show="after" @click="yes"><p>确定</p></div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      before: true,
      after: false,
      word: ''
    };
  },
  watch: {
    word() {
      if (this.word.length >= 8) {
        this.before = false;
        this.after = true;
      } else {
        this.before = true;
        this.after = false;
      }
    }
  },
  methods: {
    back() {
      this.$router.replace({ path: "/user/pass" });
    },
    yes(){
      console.log("设置密码")
    }
  }
};
</script>
<style lang="scss">
.setPass {
  height: 100%;
}
.set-top {
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
.set-content {
  height: 94%;
  background: #f3f4f6;
}
.set-title {
  font-size: 14px;
  color: #bfbfc1;
  text-align: center;
  padding: 15px;
}
.set-pass {
  background: #fff;
  height: 40px;
  display: flex;
  align-self: center;
  padding: 5px 10px;
  span {
    line-height: 40px;
  }
  input {
    outline: none;
    border: 0;
    margin-left: 10px;
    font-size: 14px;
  }
}
@mixin in {
  display: flex;
  justify-content: space-around;
  margin-top: 20px;
  p {
    width: 95%;
    text-align: center;
    height: 45px;
    line-height: 45px;
    color: #fff;
    font-size: 18px;
  }
}
.in {
  @include in;
  p {
    background: #cccccc;
  }
}
.in-to {
  @include in;
  p {
    background: #4a4c5b;
  }
}
</style>
