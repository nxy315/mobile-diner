<script>
  export default {
    created () {
      // 调用API从本地缓存中获取数据
      const logs = wx.getStorageSync('logs') || []
      logs.unshift(Date.now())
      wx.setStorageSync('logs', logs)

      console.log('app created and cache logs by setStorageSync')
    }
  }
</script>

<style>
  page {
    font-size: 26rpx;
    color: #262626;
    background-color: #f9f9f9;
  }

  * {
    box-sizing: border-box;
  }

  button {
    background-color: transparent;
    border: none;
    outline: none;
    padding: 0;
    margin: 0;
    display: inline-block;
    line-height: 1;
    font-size: 26rpx;
    border-radius: 0;
  }

  .gray {
    color: #868686;
  }

  /* flex  */
  .flex-r-sb {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }

  .flex-r-sa {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
  }

  .flex-r-c {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }

  .flex-r-fs {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
  }

  .flex-r-fe {
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    align-items: flex-end;
  }

  .flex-c-sb {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .flex-c-sa {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }

  .flex-c-c {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .flex-c-fs {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
  }

  .flex-c-fe {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
  }

  /* 文字居中 */
  .tc {
    text-align: center;
  }

  /* 购物车 */
  .cart {
    position: fixed;
    bottom: 10rpx;
    left: 40rpx;
    width: 672rpx;
    height: 94rpx;
    color: #fff;
  }

  .cart .btn {
    flex: 1;
    width: 50%;
    height: 100%;
    background-color: rgb(21, 161, 247);
    color: #fff;
    align-items: center;
  }

  .cart .btn:active {
    background-color: rgb(36, 169, 251);
  }

  .cart .btn .icon-wrap {
    position: relative;
    margin-right: 36rpx;
    width: 56rpx;
    height: 50rpx;
  }

  .cart .btn .icon-wrap .cart-icon {
    width: 100%;
    height: 100%;
  }

  .cart .btn .icon-wrap .cart-count {
    position: absolute;
    right: -12rpx;
    top: -8rpx;
    padding: 0 10rpx;
    height: 24rpx;
    line-height: 24rpx;
    text-align: center;
    border-radius: 12rpx;
    background-color: #ef624c;
    font-size: 12rpx;
  }

  .choose-btn {
    border-radius: 47rpx 0 0 47rpx;
    border-right: 1px solid #8bd0fb;
  }

  .order-btn {
    border-radius: 0 47rpx 47rpx 0;
    font-size: 34rpx;
  }

  .order-btn image {
    margin-left: 20rpx;
    width: 20rpx;
    height: 34rpx;
  }

  /* 增加减少数量 */
  .opera-btn {
    padding-right: 34rpx;
    align-items: center;
  }

  .opera-btn image {
    width: 36rpx;
    height: 36rpx;
  }

  .opera-btn image:active {
    opacity: 0.8;
  }

  .opera-btn span {
    padding: 0 24rpx;
    font-size: 32rpx;
    font-weight: bold;
    color: #333;
  }
</style>
