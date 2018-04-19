<template>
  <div class="travel">
    <Rheader name="我的行程"/>
    <div class="travel-content">
      <div class="order">已完成订单</div>
      <div>
        <ul>
          <li v-for="arr in list" class="order-list">
            <div class="list-top">
              <span>快车</span>
              <span>已完成</span>
            </div>
            <div class="time">
              <i class="iconfont icon-shijian"></i>
              <span v-text="arr.time"></span>
            </div>
            <div class="from">
              <i class="iconfont icon-yuandianxiao"></i>
              <span v-text="arr.from"></span>
            </div>
            <div class="to">
              <i class="iconfont icon-yuandianxiao"></i> 
              <span v-text="arr.to"></span>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
import Rheader from "./userHeader.vue"
import {mapActions} from 'vuex';
export default {
  data() {
    return {
      list: [
        { time: "03月17日 22:37", from: "起始地点", to: "终点位置" },
        { time: "03月17日 22:37", from: "起始地点", to: "终点位置" }
      ]
    };
  },
  components:{
    Rheader
  }
};
</script>
<style lang="scss">
.travel {
  height: 100%;
}
.travel-content {
  height: 100%;
  background: #f3f4f6;
  overflow: hidden;
  padding: 15px 10px;
  .order {
    font-size: 16px;
    color: #adadaf;
  }
}
.order-list {
  background: #fff;
  padding-top: 20px;
  padding-bottom: 15px;
  margin-top: 10px;
  box-shadow: 0 4px 3px rgba(0, 0, 0, 0.1);
  div {
    padding: 0 15px;
  }
  .iconfont {
    margin-right: 5px;
  }
  .icon-yuandianxiao {
    font-size: 12px;
  }
  .time {
    line-height: 40px;
    color: #989898;
    font-size: 15px;
    .icon-shijian {
      font-size: 12px;
    }
  }
  .from {
    color: #989898;
    font-size: 16px;
  }
  .to {
    color: #989898;
    line-height: 30px;
    .icon-yuandianxiao {
      color: #fd9059;
    }
  }
}
.list-top {
  display: flex;
  justify-content: space-between;
  span {
    &:nth-last-of-type(1) {
      color: #a0a0a0;
    }
  }
}
</style>

