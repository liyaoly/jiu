<template>
	<view>
		<uni-nav-bar background-color="#ff6666" :fixed="true" :status-bar="true">
			<view style="width: 20px;" class="headImg" slot="left">
				<image src="../../static/headIcon.png"></image>
			</view>
			<view class="searchInput" slot="default">
				<image class="search_icon" src="../../static/search_icon.png"></image>
				<input type="text" placeholder-class="placeholderClass" placeholder="请输入关键字">
			</view>

		</uni-nav-bar>
		<view class="content">
			<image class="logo" src="/static/logo.png"></image>
			<view class="text-area">
				<text class="title">{{title}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style scoped lang="scss">
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}

	.headImg {
		width: 20px;
		height: 44px;

		image {
			width: 20px;
			height: 16px;
		}
	}

	.searchInput {
		box-sizing: border-box;
		background-color: #ffffff;
		height: 32px;
		border-radius: 16px;
		display: flex;
		align-items: center;
		padding-left: 14px;
		padding-top: 6px;
		padding-bottom: 6px;

		input {
			display: inline-block;
			border-left: 1px solid #ffc2c2;
			padding-left: 10px;
			margin-left: 10px;
		}
	}

	.search_icon {
		width: 16px;
		height: 16px;
	}
</style>
