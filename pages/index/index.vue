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
			<view class='index_tab'>
				<scroll-view class="bottom_scroll" scroll-x="true" croll-with-animation="true">
					<view class="nav" v-for="(item,index) in brands" :key="index" :class="item.brand_id === choose_id?'cur':''" @tap="switchTap(item,index)">
						<view class="">{{item.brand_name}}</view>
					</view>
				</scroll-view>
			</view>
			<view class="table-head">
				<view>品名</view>
				<view>涨跌额</view>
				<view>今日参考价</view>
				<view>回收参考价</view>
			</view>
			<view class="listBox">
				<view class="itemBox"  v-for="(item,index) in dataList" :key="index"
				:class="item.status ==='rise'?'rise':item.status==='fall'? 'fall':''"
				>
					<view class="">{{item.name}}</view>
					<view class=""><text class="status">{{item.status ==='rise'?'↑':item.status==='fall'? '↓':''}}</text> {{item.change}}</view>
					<view class=""><text class="unit">￥</text> {{item.todayPrice}}</view>
					<view class=""><text class="unit">￥</text>{{item.RecoveryPrice}}</view>
				</view>
			</view>


		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				choose_id: 0,
				brands: [
					{
						brand_name: '全部',
						brand_id: 0,
						type: 'brand'
					},
					{
						brand_name: '剑南春',
						brand_id: 1,
						type: 'brand'
					}, {
						brand_name: '飞天茅台',
						brand_id: 2,
						type: 'brand'
					}, {
						brand_name: '剑南春',
						brand_id: 3,
						type: 'brand'
					}, {
						brand_name: '剑南春',
						brand_id: 4,
						type: 'brand'
					}, {
						brand_name: '剑南春',
						brand_id: 5,
						type: 'brand'
					}, {
						brand_name: '古井贡酒',
						brand_id: 6,
						type: 'brand'
					}, {
						brand_name: '剑南春',
						brand_id: 7,
						type: 'brand'
					}, {
						brand_name: '剑南春',
						brand_id: 8,
						type: 'brand'
					}, {
						brand_name: '剑南春',
						brand_id: 9,
						type: 'brand'
					}, {
						brand_name: '剑南春',
						brand_id: 10,
						type: 'brand'
					}
				],
				dataList:[
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'rise'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'fall'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'balance'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'rise'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'fall'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'balance'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'rise'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'fall'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'balance'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'rise'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'fall'
					},
					{
						name:'黑标百草香',
						change:'0.0',
						RecoveryPrice:'1600',
						todayPrice:'1900',
						status:'balance'
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			switchTap(record, index) { //更换资讯大类
				console.log(record, index)
				this.choose_id = record.brand_id

			}
		}
	}
</script>

<style scoped lang="scss">
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

	.content {


		.index_tab .bottom_scroll {
			width: 100%;
			height: 80upx;
			background: #FF6666;
			white-space: nowrap;
			overflow: hidden;
			line-height: 40rpx;
			box-sizing: border-box;
			padding: 20upx;
		}

		.index_tab .bottom_scroll .nav {
			display: inline-block;
			// min-width: 110upx;
			padding-left: 20upx;
			padding-right: 20upx;
			height: 40upx;
			background: #FB9B9B;
			box-shadow: 0px 1px 4px 0px rgba(68, 25, 25, 0.1);
			border-radius: 20px;
			white-space: normal;
			text-align: center;
			font-size: 26upx;
			font-family: SourceHanSansSC;
			font-weight: bold;
			color: #FFFFFF;
			margin-right: 30upx;
		}

		.index_tab .bottom_scroll .cur {

			background: #FFFF00;
			color: #FF6666;

		}

		.table-head {
			width: 100%;
			height: 80upx;
			background: #EEEEEE;
			font-size: 26upx;
			font-family: SourceHanSansSC;
			font-weight: bold;
			color: #333333;
			line-height: 80upx;
			display: flex;
			box-sizing: border-box;
			padding: 0 30upx;

			view {
				text-align: center;
				flex: 1;
			}

		}
		.listBox{
			width: 100%;
			height: auto;
			background: #fff;
			height: 1106upx;
			overflow-y: scroll;
			.itemBox{
				display: flex;
				justify-content: space-between;
				text-align: center;
				box-sizing: border-box;
				padding:0 40upx;
				height: 116upx;
				line-height: 116upx;
				border: 1px solid #EEEEEE;
				font-size: 26upx;
				font-family: SourceHanSansSC;
				font-weight: 500;
				color: #666666;
				.status,.unit {
					margin-right: 10upx;
					font-size: 20upx;
				}
				
			}
			.rise{
				
				color: #FF6666;
				
			}
			.fall{
				
				color: #0066CC;
				
			}
		}
	}
</style>
