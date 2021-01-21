<template>
	<view>
		
	</view>
</template>
<script>
	// import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue"
	export default {
		// components: {uniNavBar},
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	/*每个页面公共css */
	.placeholderClass{
		color: #aaaaaa;
	}
	.headImg {
		width: 20px;
		height: 44px;
	
		image {
			width: 20px;
			height: 16px;
		}
	}
</style>
