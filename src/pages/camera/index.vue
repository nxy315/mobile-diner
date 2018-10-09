<template>
  <div>
		<camera v-if='visible' device-position="front" flash="off" binderror="error" style="width: 100%; height: 600px;">
			<cover-image class='take-photo' src='/static/images/face.png' @click="takePhoto"></cover-image>
			<cover-view>请正面对准摄像头扫描区域</cover-view>
			<cover-view>光线自然，无过度曝光或强逆光</cover-view>
			<cover-view>人脸不存在遮挡（墨镜或其他遮挡物）</cover-view>
		</camera>
		<image @click='hidecamera' mode="widthFix" :src="src"></image>
  </div>
</template>

<script>

export default {
	data () {
		return {
			src: '',
    	visible: true
		}
	},
  methods: {
		takePhoto() {
			const ctx = wx.createCameraContext()
			ctx.takePhoto({
				quality: 'high',
				success: (res) => {
					this.setData({
						src: res.tempImagePath
					})
				}
			})
		},
		error(e) {
			console.log(e.detail)
		},
		hidecamera() {
			this.setData({
				visible: false
			})
		},
  }
}
</script>

<style scoped>
.take-photo{
  position: relative;
  left: 284rpx;
  top: 900rpx;
  width: 184rpx;
  height: 184rpx;
  border-radius: 50%;
}
</style>
