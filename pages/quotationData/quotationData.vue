<template>
	<view class="quotationChart">
		<!-- 自定义头部板块 -->
		<uni-nav-bar left-icon="back" background-color="#ff6666" title="行情" color='#fff' :fixed="true" :status-bar="true"
		 @clickLeft='onClickLeft'>
		
		</uni-nav-bar>
		<view class="content">
			<view class="total">
				<view class="moneyBox">{{money}}</view>
				<view class="changeBox">
					<view>{{num_val>0?'+':''}}{{num_val}}</view>
					<view>{{percent_val>0?'+':''}}{{percent_val}}%</view>
				</view>
				<view class="follow">+ 关注</view>
			</view>
			<view class="table-head">
				<view class="firstBox">品名</view>
				<view class="secondBox">2020/01/20</view>
				<view class="thirdBox">2020/01/21</view>
				<view class="fourBox">涨跌</view>
			</view>
			<view class="listBox">
				<view class="itemBox"  v-for="(item,index) in dataList" :key="index">
					<view class="firstBox">{{item.name}}</view>
					<view class="secondBox"><text class="unit">￥</text>{{item.price_yesterday}}</view>
					<view class="thirdBox"><text class="unit">￥</text>{{item.price_today}}</view>
					<view class="fourBox" :class="item.status"><text :class="item.status"></text>{{item.change>0?'+':''}}{{item.change}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// total
				money: 15200,
				num_val: 900,
				percent_val: 60.09,
				
				dataList: [
					{
						name: '2020飞天茅台',
						price_yesterday: '2980',
						price_today: '2990',
						change: '10',
						status: 'rise'
					},
					{
						name: '2020飞天茅台(散瓶)',
						price_yesterday: '2460',
						price_today: '2450',
						change: '-10',
						status: 'fall'
					},
					{
						name: '2020飞天茅台',
						price_yesterday: '2980',
						price_today: '2990',
						change: '10',
						status: 'rise'
					},
					{
						name: '2020飞天茅台(散瓶)',
						price_yesterday: '2460',
						price_today: '2450',
						change: '-10',
						status: 'fall'
					},{
						name: '2020飞天茅台',
						price_yesterday: '2980',
						price_today: '2990',
						change: '10',
						status: 'rise'
					},
					{
						name: '2020飞天茅台(散瓶)',
						price_yesterday: '2460',
						price_today: '2450',
						change: '-10',
						status: 'fall'
					},{
						name: '2020飞天茅台',
						price_yesterday: '2980',
						price_today: '2990',
						change: '10',
						status: 'rise'
					},
					{
						name: '2020飞天茅台(散瓶)',
						price_yesterday: '2460',
						price_today: '2450',
						change: '-10',
						status: 'fall'
					},{
						name: '2020飞天茅台',
						price_yesterday: '2980',
						price_today: '2990',
						change: '10',
						status: 'rise'
					},
					{
						name: '2020飞天茅台(散瓶)',
						price_yesterday: '2460',
						price_today: '2450',
						change: '-10',
						status: 'fall'
					},
					{
						name: '2020飞天茅台(散瓶)',
						price_yesterday: '2460',
						price_today: '2460',
						change: '0',
						status: 'nochange'
					}
				]
			}
		},
		methods: {
			onClickLeft(e) {
				uni.navigateBack({
					delta: 1
				});
			
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content {
		.total {
			width: 100%;
			height: 150upx;
			background: #FF6666;
			.moneyBox{
				width: 30%;
				height: 150upx;
				line-height: 150upx;
				text-align: right;
				font-size: 48upx;
				font-family: MicrosoftYaHeiUI;
				font-weight: bold;
				color: #FFFFFF;
				float: left;
			}
			.changeBox{
				float: left;
				width: 20%;
				height: 150upx;
				vertical-align: middle;
				display: flex;
				flex-direction: column;
				justify-content: center;
				padding-left: 20upx;
				view{	
					margin-top: 10upx;
					margin-bottom: 10upx;
					font-size: 26upx;
					font-family: MicrosoftYaHeiUI;
					font-weight: 400;
					color: #FFFFFF;
				}
			}
			.follow{
				float: left;
				margin-left: calc(25% - 76upx);
				margin-top: 41upx;
				width: 150upx;
				height: 64upx;
				border: 2upx solid #FFFFFF;
				border-radius: 8upx;
				font-size: 30upx;
				font-family: SourceHanSansSC;
				font-weight: 400;
				color: #FFFFFF;
				text-align: center;
				line-height: 64upx;
			}
		}
		.table-head {
			width: 100%;
			height: 80upx;
			background: #EEEEEE;
			font-size: 24upx;
			font-family: SourceHanSansSC;
			font-weight: bold;
			color: #333333;
			line-height: 80upx;
			display: flex;
			box-sizing: border-box;
			padding: 0 30upx;
		}
		.listBox{
			width: 100%;
			height: auto;
			background: #fff;
			height: 1106upx;
			overflow-y: scroll;
			
			.itemBox{
				flex: 1;
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
		.firstBox{
			width: 40%;
			text-align: left;
		}
		.secondBox,.thirdBox{
			width: 25%;
			text-align: center;
		}
		.fourBox{
			width: 10%;
			text-align: right;
		}
	}
</style>
