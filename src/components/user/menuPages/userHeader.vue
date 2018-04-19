<template>
  <div class="top">
    <i class="iconfont icon-zuojiantou" @click="back"></i>
    <p>{{name}}</p>
    <div></div>
  </div>
</template>
<script>
export default {
  props: ["name"],
  methods: {
    back() {
      this.$router.go(-1);
      this.$store.dispatch("close_usersidebar");
    }
  }
};
</script>
<style lang="scss">
.top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 6%;
  font-size: 18px;
  padding: 0 15px;
  color: #353535;
  .icon-zuojiantou {
    font-size: 18px;
  }
}
</style>
