<template>
  <div>
    <!-- 堂食外带 -->
    <div class="place-container flex-r-fs">
      <div class="place-wrap flex-r-sa">
        <div class="place-item flex-r-c" @click="choosePlace(1)">
          <image mode="aspectFit" :src="png1" style="width:38rpx;height:28rpx;"/>
          <span :style="{color: color1}">堂食</span>
        </div>
        <div class="place-item flex-r-c" @click="choosePlace(2)">
          <image mode="aspectFit" :src="png2" style="width:30rpx;height:28rpx;"/>
          <span :style="{color: color2}">外带</span>
        </div>
        <!--<div class="active-bg active-bg1" :style="{left: left}" :class="{left: current, right: !current}"></div>-->
        <div class="active-bg active-bg2" :style="{left: left}" :class="{left: current, right: !current}"></div>
      </div>
      <div class="bg"></div>
    </div>

    <!-- 就餐时间 -->
    <div class="choose-time-wrap flex-c-fs">
      <div class="title flex-r-fs">
        <image src="/static/images/clock.png"/>
        <span>就餐时段</span>
      </div>
      <div></div>
    </div>

    <!-- 订单列表 -->
    <div class="order-list">
      <div class="order-wrap">
        <div class="order-item flex-r-sb" v-for="(item, index) in order" :key="index">
          <span>{{item.name}}</span>
          <div class="flex-r-fs">
            <strong class="flex-r-fs item-price"><span>￥</span><span>{{item.price}}</span></strong>
            <div class='opera-btn flex-r-fs' style="padding: 0;">
              <image src='/static/images/reduce.png'></image>
              <span>{{item.count}}</span>
              <image src='/static/images/add.png'></image>
            </div>
          </div>
        </div>
      </div>
      <div class="order-price flex-r-sb">
        <span>合计</span>
        <span class="total-price flex-r-fs"><span>￥</span><span>28.8</span></span>
      </div>
    </div>

    <!-- 购物车底部fixed -->
    <div class='cart flex-r-fs' style='bottom: 36rpx;'>
      <div class='btn choose-btn flex-r-c'>
        <div class='icon-wrap'>
          <image class='cart-icon' src='/static/images/menu_cart_icon.png'/>
          <span class='cart-count'>1</span>
        </div>
        <span>￥28.8</span>
      </div>
      <div class='btn order-btn flex-r-c' @click='pay'>
        <span>确认支付</span>
      </div>
    </div>
  </div>
</template>

<script>

  export default {
    data () {
      return {
        place: 1, // 1堂食 2外带
        order: [
          {name: '加浓美式1', price: 27, count: 1},
          {name: '加浓美式2', price: 28, count: 1},
          {name: '加浓美式3', price: 29, count: 2},
        ]
      }
    },
    methods: {
      /**
       * 支付
       */
      pay() {
        wx.navigateTo({
          url: '/pages/pay-result/main',
        })
      },
      choosePlace(place) {
        this.place = place
      }
    },
    computed: {
      current() {
        return this.place === 1;
      },
      png1() {
        return this.place === 1 ? '/static/images/dine_active.png' : '/static/images/dine.png'
      },
      png2() {
        return this.place === 2 ? '/static/images/takeaway_active.png' : '/static/images/takeaway.png'
      },
      color1() {
        return this.place === 1 ? '#169ff7' : '#fff'
      },
      color2() {
        return this.place === 2 ? '#169ff7' : '#fff'
      },
      left() {
        return this.place === 2 ? '240rpx' : '11rpx'
      }
    }
  }
</script>

<style lang="less" scoped>
  @keyframes move1 {
    0% {
      left: 11rpx;
    }
    100% {
      left: 240rpx;
    }
  }

  @keyframes move2 {
    0% {
      left: 240rpx;
    }
    100% {
      left: 11rpx;
    }
  }

  /* 堂食外带 */
  .place-container {
    position: relative;
    padding: 0 20rpx;
    height: 124rpx;
    background-color: #169ff7;
    .place-wrap {
      box-sizing: border-box;
      position: relative;
      width: 478rpx;
      height: 80rpx;
      border-radius: 80rpx;
      border: 1rpx solid #fff;
      align-items: center;
      .place-item {
        position: relative;
        z-index: 2;
        width: 50%;
        image {
          margin-right: 27rpx;
        }
        span {
          color: #fff;
        }
      }
      .active-bg {
        position: absolute;
        // top: 9rpx;
        width: 224rpx;
        height: 60rpx;
        background-color: #fff;
        border-radius: 30rpx;
        z-index: 1;

      }
      .active-bg1 {
        &.left {
          animation: move2 2s ease .8s;
          animation-fill-mode: forwards;
        }
        &.right {
          animation: move1 2s ease .8s;
          animation-fill-mode: forwards;
        }
      }
      .active-bg2 {
        &.left {
          animation: move2 .2s ease-out;
          animation-fill-mode: forwards;
        }
        &.right {
          animation: move1 .2s ease-out;
          animation-fill-mode: forwards;
        }
      }
    }
    .bg {
      position: absolute;
      left: 0;
      bottom: -154rpx;
      width: 100%;
      height: 160rpx;
      background-color: #169ff7;
    }
  }

  /* 选择时间 */
  .choose-time-wrap {
    position: relative;
    margin: 0 auto;
    width: 710rpx;
    height: 266rpx;
    background-color: #fff;
    border-radius: 16rpx;
    box-shadow: 0 5rpx 50rpx 0 rgba(0, 0, 0, 0.1);
    z-index: 2;

    .title {
      padding: 0 20rpx;
      height: 70rpx;
      border-bottom: 2rpx solid #f3f3f3;
      font-size: 28rpx;

      image {
        margin-right: 13rpx;
        width: 24rpx;
        height: 24rpx;
      }
    }
  }

  /* 订单列表 */
  .order-list {
    margin-top: 30rpx;
    padding: 0 30rpx;
    background-color: #fff;
    font-size: 26rpx;

    .order-wrap {
      padding: 19rpx 0;

      .order-item {
        height: 64rpx;

        .item-price {
          margin-right: 32rpx;
          align-items: flex-end;
          color: #f0644e;
          span:first-child {
            font-size: 20rpx;
          }
          span:last-child {
            font-weight: 400;
          }
        }
      }
    }

    .order-price {
      height: 88rpx;
      border-top: 2rpx solid #f0f0f0;
      .total-price {
        align-items: flex-end;
        span:first-child {

        }
        span:last-child {
          font-size: 32rpx;
        }
      }
    }
  }
</style>
