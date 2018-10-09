<template>
  <!-- 购物车底部fixed -->
	<div class='cart flex-r-fs' style='bottom: 36rpx;'>
		<div class='btn choose-btn flex-r-c'>
			<div class='icon-wrap'>
				<image class='cart-icon' src='/static/images/menu_cart_icon.png'/>
				<span class='cart-count'>1</span>  
			</div>
			<span>￥28.8</span>
		</div>
		<div class='btn order-btn flex-r-c' @click='pay' >
			<span>确认支付</span>
		</div>
	</div>
</template>

<script>

export default {
	data () {
		return {
			
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
  }
}
</script>

<style scoped>
page{
  background-color: #f9f9f9;
}
</style>
