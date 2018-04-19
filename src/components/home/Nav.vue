<template>
  <div class="tab-wrapper"> 
    <div class="fast"><span>快车</span></div>
  </div>
</template>
<script>
import { mapGetters, mapActions } from "vuex";
export default {
  computed: {
    navList() {
      return this.$store.state.navList;
    }
  },
  methods: {
    switch_nav(index) {
      return this.$store.dispatch("switch_nav", index);
    }
  }
};
</script>
<style lang="scss">
.fast{
  font-size: 18px;
  span{
    margin-left: 38%;
  }
}
a {
  text-decoration: none;
}
.navigator .nav-wrapper .tab-wrapper {
  position: relative;
  z-index: 50;
  line-height: 54px;
  overflow: hidden;
  white-space: nowrap;
  -webkit-box-flex: 1;
  -ms-flex: 1;
  flex: 1;
}

.navigator .nav-wrapper .tab-wrapper .nav-mask {
  position: absolute;
  z-index: 10;
  height: 100%;
  width: 14px;
  pointer-events: none;
}

.navigator .nav-wrapper .tab-wrapper .mask-left {
  left: 0;
  background: -webkit-linear-gradient(left, #fff, hsla(0, 0%, 100%, 0));
  background: linear-gradient(left, #fff, hsla(0, 0%, 100%, 0));
}

.navigator .nav-wrapper .tab-wrapper .mask-right {
  right: 0;
  background: -webkit-linear-gradient(right, #fff, hsla(0, 0%, 100%, 0));
  background: linear-gradient(right, #fff, hsla(0, 0%, 100%, 0));
}

.navigator .nav-wrapper .tab-wrapper .tab-list {
  margin: 0 auto;
}

.navigator .nav-wrapper .tab-wrapper .tab-list .tab-item {
  display: inline-block;
}

.navigator .nav-wrapper .tab-wrapper .tab-list .tab-item .tab-name {
  display: block;
  position: relative;
  padding: 0 15px 0 14px;
  font-size: 14px;
}

.navigator .nav-wrapper .tab-wrapper .tab-list .tab-item .tab-name a {
  color: #4a4c5b;
}

.navigator
  .nav-wrapper
  .tab-wrapper
  .tab-list
  .tab-item
  .tab-name
  .link-active {
  -webkit-transition: all 0.2s;
  transition: all 0.2s;
  /*-webkit-transform: scale(1.14);
  transform: scale(1.14);*/
  color: #fc9153;
}
  .navigator
  .nav-wrapper
  .tab-wrapper
  .tab-list
  .tab-item
  .tab-name.link-unactive {
}
</style>
