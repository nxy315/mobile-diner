<template>
  <div>
    <div class="choose-time-wrap flex-c-fs">
      <div class="title flex-r-fs">
        <image src="/static/images/clock.png"/>
        <span>就餐时段</span>
      </div>
      <div></div>
    </div>

    <!-- 购物车底部fixed -->
    <div class='cart flex-r-fs'>
      <div class='btn choose-btn flex-r-c'>
        <div class='icon-wrap'>
          <image class='cart-icon' src='/static/images/menu_cart_icon.png'></image>
          <span class='cart-count'>1</span>
        </div>
        <span>￥28.8</span>
      </div>
      <div class='btn order-btn flex-r-c' @click='makeOrder'>
        <span>选好了</span>
        <image src='/static/images/right_arrow.png'></image>
      </div>
    </div>
  </div>
</template>

<script>

  export default {
    data () {
      return {
        text: 1
      }
    },
    methods: {}
  }
</script>

<style lang="less" scoped>
  .choose-time-wrap {
    width: 710rpx;
    height: 266rpx;
    background-color: #fff;
    border-radius: 16rpx;
    box-shadow: 0 10rpx 20rpx 10rpx #ccc;
  }
</style>
