<template>
  <div class="pass">
    <div class="pass-top">
        <i class="iconfont icon-zuojiantou" @click="back"></i>
        <p>安全认证</p>
        <div></div>
    </div>
    <div class="pass-content">
        <div class="phone">设置密码需先验证您的手机号{{phone}}</div>
        <div class="code">
            <span>验证码</span>
            <input type="tel" maxlength="4" placeholder="请输入验证码" v-model="word"/>
            <button @click="code" v-show="bool">获取验证码</button>
            <div class="time-again" v-show="boll">{{time}}秒后重发</div>
            <div class="again" v-show="bllo" @click="again">重新发送</div>
        </div>
        <div class="next" v-show="btn1"><p>下一步</p></div>
        <div class="next-btn" v-show="btn2" @click="set"><p>下一步</p></div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      phone: "",
      word:'',
      time: 60,
      boll: false,
      bool: true,
      bllo: false,
      timer: null,
      btn1: true,
      btn2: false 
    };
  },
  watch:{
    word(){
        if(this.word.length==4){
            this.btn1 = false;
            this.btn2 = true; 
        }else{
            this.btn1 = true;
            this.btn2 = false;
        }
    }
  },
  mounted() {
    this.phone = localStorage.getItem("telephone");
    this.phone = this.phone.substr(0, 3) + "****" + this.phone.substr(7);
  },
  methods: {
    back() {
      this.$router.replace({ path: "/user/setting" });
      this.$store.dispatch("close_usersidebar");
    },
    timed() {
      var self = this;
      self.timer = setInterval(function() {
        if (self.time <= 0) {
          self.boll = !self.boll;
          self.bllo = !self.bllo;
          clearInterval(self.timer);
          self.time = 60;
        } else {
          self.time--;
        }
      }, 1000);
    },
    code() {
      this.boll = !this.boll;
      this.bool = !this.bool;
      this.timed();
    },
    again() {
      this.boll = !this.boll;
      this.bllo = !this.bllo;
      this.timed();
    },
    set(){
        this.$router.replace({path:'/user/setpass'})
    }
  }
};
</script>
<style lang="scss">
.pass {
  height: 100%;
}
.pass-top {
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
.pass-content {
  height: 94%;
  background: #f3f4f6;
}
.phone {
  font-size: 14px;
  color: #bfbfc1;
  text-align: center;
  padding: 15px;
}
.code {
  background: #fff;
  display: flex;
  justify-content: space-between;
  height: 40px;
  align-items: center;
  padding: 5px 10px;
  span {
    font-size: 14px;
    color: #707070;
    font-weight: 600;
  }
  input {
    outline: none;
    border: 0;
    padding-left: 5px;
    width: 45%;
  }
  @mixin btn {
    height: 80%;
    background: #fff;
    outline: none;
    border: 1px solid #bfbfbf;
    width: 25%;
    font-size: 12px;
    color: #a0a0a0;
    border-radius: 4px;
  }
  button {
    @include btn;
  }
  .time-again {
    @include btn;
    justify-content: space-around;
    display: flex;
    align-items: center;
  }
  .again {
    @include btn;
    justify-content: space-around;
    display: flex;
    align-items: center;
  }
}
@mixin next{
    display: flex;
    justify-content: center;
    margin-top: 20px;
    p{
        width: 90%;
        text-align: center;
        height: 40px;
        line-height: 40px;
        color: #fff;
    }
}
.next{
    @include next;
    p{
        background: #CCCCCC;
    }
}
.next-btn{
    @include next;
    p{
        background: #4A4C5B;
    }
}
</style>
