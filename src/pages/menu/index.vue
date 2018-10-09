<template>
  <div>
		<!-- 菜单banner -->
		<div class='banner'>
			<image class='road' src='/static/images/road.png'></image>
			<image class='city' src='/static/images/city.png'></image>
			<image class='car' src='/static/images/car.png'></image>
		</div>

		<!-- 商品列表 -->
		<div class='commodity-list'>
			<div class='commodity-wrap flex-r-fs' v-for='(item, index) in list' :key='index'>
				<image mode='aspectFill' class='cover' src='/static/images/cover.png'></image>
				<div class='content flex-c-sb'>
					<div class='des flex-c-fs'>
						<span class='title'>{{item.name}}</span>
						<span class='info'>{{item.info}}</span>
					</div>
					<div class='foot flex-r-sb'>
						<span class='price-wrap flex-r-fe'>
							<span class='unit'>￥</span>
							<span class='price'>{{item.price}}</span>
						</span>
						<div class='opera-btn flex-r-fs'>
							<image src='/static/images/reduce.png'></image>
							<span>0</span>
							<image src='/static/images/add.png'></image>
						</div>
					</div>
				</div>
			</div>
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
			list: [
      {
        name: '华夫套餐-早餐限定',
        info: '华夫饼、九珍果汁（大）',
        price: '37.2'
      },
      {
        name: '华夫套餐-早餐限定',
        info: '华夫饼、九珍果汁（大）',
        price: '37.2'
      },
      {
        name: '华夫套餐-早餐限定',
        info: '华夫饼、九珍果汁（大）',
        price: '37.2'
      },
      {
        name: '华夫套餐-早餐限定',
        info: '华夫饼、九珍果汁（大）',
        price: '37.2'
      },
      {
        name: '华夫套餐-早餐限定',
        info: '华夫饼、九珍果汁（大）',
        price: '37.2'
      },
      {
        name: '华夫套餐-早餐限定',
        info: '华夫饼、九珍果汁（大）',
        price: '37.2'
      },
    ]
		}
	},
  methods: {
		/**
		 * 生成订单 
		 */
		makeOrder() {
			wx.navigateTo({
				url: '/pages/order/main',
			})
		},
  }
}
</script>

<style scoped>
/* 顶部banner */
.banner{
  position: relative;
  height: 350rpx;
  background-color: #deefff;
}
.banner .road{
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 52rpx;
}
.banner .city{
  position: absolute;
  left: 0;
  bottom: 50rpx;
  width: 100%;
  height: 255rpx;
}
.banner .car{
  position: absolute;
  left: 60rpx;
  bottom: 40rpx;
  width: 280rpx;
  height: 90rpx;
}

/* 商品列表 */
.commodity-list{
  padding: 0 36rpx 100rpx;
  background-color: #f9f9f9;
}
.commodity-list .commodity-wrap{
  padding: 21rpx 0;
  height: 244rpx;
  border-bottom: 1rpx solid #f0f0f0;
}
.commodity-list .commodity-wrap .cover{
  margin-right: 25rpx;
  width: 200rpx;
  height: 200rpx;
}
.commodity-list .commodity-wrap .content{
  flex: 1;
  height: 200rpx;
  align-items: flex-start;
}
.commodity-list .commodity-wrap .content .des .title{
  margin-bottom: 10rpx;
  height: 52rpx;
  line-height: 52rpx;
  font-size: 32rpx;
  color: #333;
}
.commodity-list .commodity-wrap .content .des .info{
  line-height: 36rpx;
  font-size: 24rpx;
  color: #999;
}
.commodity-list .commodity-wrap .content .foot{
  margin-bottom: 18rpx;
  width: 100%;
  height: 36rpx;
  align-items: center;
}
.commodity-list .commodity-wrap .content .foot .price-wrap{
  color: #ef624c;
}
.commodity-list .commodity-wrap .content .foot .price-wrap .unit{
  font-size: 18rpx;
}
.commodity-list .commodity-wrap .content .foot .price-wrap .price{
  font-size: 32rpx;
  font-weight: bold;
}
.commodity-list .commodity-wrap .content .foot .opera-btn{
  padding-right: 34rpx;
  align-items: center;
}
.commodity-list .commodity-wrap .content .foot .opera-btn image{
  width: 36rpx;
  height: 36rpx;
}
.commodity-list .commodity-wrap .content .foot .opera-btn image:active{
  opacity: 0.8;
}
.commodity-list .commodity-wrap .content .foot .opera-btn span{
  padding: 0 24rpx;
  font-size: 32rpx;
  font-weight: bold;
  color: #333;
}
</style>
