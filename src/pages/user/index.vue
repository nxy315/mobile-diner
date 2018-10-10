<template>
  <div>
    <!-- 我的 背景 -->
    <div class='user-bg'></div>

    <div class='user-body'>
      <!-- 头部用户信息 -->
      <div class='user-head flex-r-sb'>
        <div class='user-cover-wrap flex-r-fs'>
          <image class='user-cover' src='/static/images/cover.png'></image>
          <span>深兰科技</span>
        </div>
      </div>

      <!-- 券码列表 -->
      <div class='coupon-list'>
        <div class='list-bg'></div>
        <div class='coupon-item flex-c-fs' v-for='(item, index) in list' :key='index' @click='toDetail'>
          <image class='bg' src='/static/images/coupon-bg1.png'></image>
          <image class='dashed' src='/static/images/dashed.png'></image>
          <div class='coupon-head flex-r-sb'>
            <div class='time flex-r-fs'>
              <image src='/static/images/clock.png'></image>
              <span>{{item.time}}</span>
            </div>
            <span>{{item.type === 1 ? '堂食' : '外带'}}</span>
          </div>

          <div class='coupon-content'>
            <div class='coupon-num flex-r-c'>券码：{{item.num}}</div>
            <div class='coupon-foot flex-r-sb'>
              <span>{{item.name}}</span>
              <div class='price flex-r-fe'>
                <span>￥</span>
                <span>{{item.price}}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

  export default {
    data () {
      return {
        list: [
          {time: '2018-08-23 上午 09:30', type: 1, num: 132323, name: '华夫套餐-早餐限定', price: 37.2},
          {time: '2018-08-23 上午 09:30', type: 2, num: 132323, name: '华夫套餐-早餐限定', price: 37.2},
          {time: '2018-08-23 上午 09:30', type: 1, num: 132323, name: '华夫套餐-早餐限定', price: 37.2}
        ]
      }
    },
    methods: {
      /**
       * 跳转券码详情页
       */
      toDetail() {
        wx.navigateTo({
          url: '/pages/coupon-detail/main',
        })
      },
    }
  }
</script>

<style lang='less' scoped>
  page {
    background-color: #f9f9f9;
  }

  /* 用户头像 */
  .user-head {
    padding: 0 20rpx;
    height: 190rpx;
    background-color: #169ef7;
  }

  .user-cover {
    margin-left: 15rpx;
    margin-right: 38rpx;
    width: 148rpx;
    height: 148rpx;
    border-radius: 50%;
    border: 4rpx solid #fff;
  }

  .user-cover-wrap span {
    color: #fff;
    font-size: 28rpx;
  }

  /* 优惠券列表 */
  .coupon-list {
    position: relative;
    width: 100%;
  }

  .coupon-list .list-bg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100rpx;
    background-color: #169ef7;
    z-index: 1;
  }

  .coupon-item {
    position: relative;
    height: 268rpx;
    background-repeat: no-repeat;
    background-position: left top;
    background-size: 100%;
  }

  .coupon-item .bg {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 110%;
    z-index: 1;
  }

  .coupon-item .dashed {
    position: absolute;
    left: 48rpx;
    top: 75rpx;
    width: 650rpx;
    height: 4rpx;
    z-index: 2;
  }

  .coupon-item .coupon-head {
    position: relative;
    padding: 0 61rpx;
    height: 96rpx;
    color: #592e26;
    font-size: 24rpx;
    z-index: 3;
  }

  .coupon-item .coupon-head .time {

  }

  .coupon-item .coupon-head .time image {
    margin-right: 24rpx;
    width: 38rpx;
    height: 36rpx;
  }

  .coupon-item .coupon-head .time image span {

  }

  .coupon-item .coupon-content {
    position: relative;
    z-index: 3;
  }

  .coupon-item .coupon-content .coupon-num {
    height: 80rpx;
    color: #592e26;
    font-weight: 400;
    font-size: 36rpx;
  }

  .coupon-item .coupon-content .coupon-foot {
    padding: 0 118rpx;
    margin-top: 12rpx;
    height: 60rpx;
    font-size: 24rpx;
    color: #989898;
  }

  .coupon-item .coupon-content .coupon-foot .price span {
    color: #f85766;
  }

  .coupon-item .coupon-content .coupon-foot .price span:last-child {
    font-size: 28rpx;
    font-weight: 400;
  }
</style>
