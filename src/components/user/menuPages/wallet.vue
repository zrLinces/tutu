<template>
  <div class="wallet">
    <Rheader name="钱包" />
    <div class="wallet-content">

    </div>
  </div>
</template>
<script>
import Rheader from "./userHeader.vue"
export default {
  components:{
    Rheader
  }
}
</script>
<style lang="scss">
.wallet{
  height: 100%;
  .wallet-content{
    height: 100%;
    background: #f3f4f6;
  }
}
</style>