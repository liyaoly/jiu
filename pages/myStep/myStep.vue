<template>
	<view class="myFocus">
		<uni-nav-bar left-icon="back" background-color="#ff6666" title="我的关注" color='#fff' :fixed="true" :status-bar="true"
		 @clickLeft='onClickLeft'>
			<view style="width: 20px;" class="headImg" slot="left">
				<image src="../../static/headIcon.png"></image>
			</view>
		</uni-nav-bar>
		<view class="content">
			<view class="tabar">
				<view class="tabar-item" :class="showTab==='brand'?'tabar-item-active':''" @tap="changeTo('brand')">品牌</view>
				<view class="tabar-item" :class="showTab==='product'?'tabar-item-active':''" @tap="changeTo('product')">产品</view>
			</view>
			<view class="listBox">

				<view class="brand" :class="showTab==='brand'?'':'brand-hide'">
					<view class="itemBox" v-for="(item,index) in brand" :key="index" :class="index%2===0?'marginRight':''">
						<view class="close">x</view>
						<view class=""><text class="name">{{item.name}}</text>
							<uni-icons type="top"></uni-icons>
							<text :class="item.status ==='up'?'pointup':'pointdown'">{{item.status ==='up'?'↑':'↓'}}</text>
						</view>
						<view class="displayBox"><text class="typeLabel">品牌</text><text class="focusTime">{{item.time}}</text></view>
						<view class="displayBox">
							<text :class="item.status ==='up'?'rangeup':'rangedown'">{{item.status ==='up'?'+':"-"}}{{item.range}}</text>
							<view class="">
								<text class="unit">￥</text>
								<text class="price">{{item.price}}</text>
							</view>
						</view>
					</view>
				</view>
				<view class="product" :class="showTab==='product'?'':'product-hide'">
					<view class="itemBox" v-for="(item,index) in product" :key="index" :class="index%2===0?'marginRight':''">
						<view class="close">x</view>
						<view class="">
							<text class="name">{{item.name}}</text>
							<text :class="item.status ==='up'?'pointup':'pointdown'">{{item.status ==='up'?'↑':'↓'}}</text>
							<!-- <uni-icons type="top"></uni-icons> -->
						</view>
						<view class="displayBox"><text class="typeLabel">品牌</text><text class="focusTime">{{item.time}}</text></view>
						<view class="displayBox">
							<text :class="item.status ==='up'?'rangeup':'rangedown'">{{item.status ==='up'?'+':"-"}}{{item.range}}</text>
							<view class="">
								<text class="unit">￥</text>
								<text class="price">{{item.price}}</text>
							</view>
						</view>
					</view>

				</view>
			</view>

		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				showTab: 'brand',
				brand: [{
						name: '古井贡酒',
						time: '12天前关注',
						status: 'down',
						range: '40%',
						price: 5978
					},
					{
						name: '贵州茅台',
						time: '12天前关注',
						status: 'up',
						range: '40%',
						price: 1299
					},
					{
						name: '古井贡酒',
						time: '12天前关注',
						status: 'up',
						range: '40%',
						price: 5978
					},
					{
						name: '贵州茅台',
						time: '12天前关注',
						status: 'up',
						range: '40%',
						price: 1299
					},
					{
						name: '古井贡酒',
						time: '12天前关注',
						status: 'up',
						range: '40%',
						price: 5978
					},
					{
						name: '贵州茅台',
						time: '12天前关注',
						status: 'up',
						range: '40%',
						price: 1299
					},
					{
						name: '古井贡酒',
						time: '12天前关注',
						status: 'top',
						range: '40%',
						price: 5978
					},
					{
						name: '贵州茅台',
						time: '12天前关注',
						status: 'up',
						range: '40%',
						price: 1299
					},
					{
						name: '古井贡酒',
						time: '12天前关注',
						status: 'top',
						range: '40%',
						price: 5978
					},
					{
						name: '贵州茅台',
						time: '12天前关注',
						status: 'up',
						range: '40%',
						price: 1299
					},
					{
						name: '古井贡酒',
						time: '12天前关注',
						status: 'top',
						range: '40%',
						price: 5978
					},
					{
						name: '贵州茅台',
						time: '12天前关注',
						status: 'up',
						range: '40%',
						price: 1299
					},

				],
				product: [{
					name: '古井贡酒',
					time: '12天前关注',
					status: 'top',
					range: '40%',
					price: 5978
				}, ]

			}
		},
		methods: {
			changeTo(type) {
				this.showTab = type
				console.log(type)
			},
			onClickLeft(e) {
				uni.navigateBack({
					delta: 1
				});

			}
		}
	}
</script>

<style scoped lang="scss">
	.myFocus {
		.content {
			background: #eee;
			.tabar {
				width: 750upx;
				height: 100upx;
				background: #FFFFFF;
				display: flex;
				text-align: center;
				justify-content: space-between;
				line-height: 100upx;
				.tabar-item {
					flex: 1;
					font-size: 30upx;
					font-family: SourceHanSansSC;
					font-weight: 400;
					color: #666666;
				}
				.tabar-item-active {
					border-bottom: 2px solid #0066CC;
					font-weight: bold;
					color: #0066CC;
				}

			}

			.listBox {
				width: 100%;
				min-height: 1106upx;
				overflow-x: hidden;
				overflow-y: scroll;
				position: relative;
				.brand,
				.product {
					width: 100%;
					height: auto;
					box-sizing: border-box;
					padding: 40upx;
					background: #EEEEEE;
					position: absolute;
					transform: translateX(0);
					transition: all 0.5s;
					display: flex;
					flex-wrap: wrap;

					.itemBox {
						width: 315upx;
						height: 218upx;
						background: #FFFFFF;
						border-radius: 8upx;
						margin-bottom: 40upx;
						box-sizing: border-box;
						padding: 40upx 30upx;
						display: flex;
						flex-direction: column;
						justify-content: space-between;
						position: relative;

						.close {
							position: absolute;
							right: 0;
							top: 0;
							width: 53upx;
							height: 51upx;
							background: #333333;
							border-bottom-left-radius: 100%;
							opacity: 0.4;
							text-align: center;
							line-height: 30upx;
							color: #fff;
						}

						.displayBox {
							display: flex;
							justify-content: space-between;
						}

						.name {
							font-size: 36upx;
							font-weight: bold;
							color: #333333;

						}

						.typeLabel {
							display: inline-block;
							width: 100upx;
							height: 24upx;
							background: #333333;
							border-radius: 12px;
							font-size: 20upx;
							font-family: SourceHanSansSC;
							color: #FFFFFF;
							text-align: center;
							margin-right: 10upx;
						}

						.focusTime {
							font-size: 20upx;
							color: #666666;

						}

						.rangeup,.pointup {
							font-size: 26upx;
							font-weight: 600;
							color: #FF6666;
						}
						.rangedown,.pointdown{
							font-size: 26upx;
							font-weight: 600;
							color: #0066CC;
						}
						.pointup,.pointdown{
							font-size: 20upx;
							margin-left: 10upx;
						}

						.unit {
							font-size: 20upx;
							font-weight: bold;
							color: #FF6666;
						}

						.price {

							font-size: 30upx;
							font-weight: bold;
							color: #FF6666;
						}

					}

					.marginRight {
						margin-right: 40upx;
					}

				}

				.brand-hide {
					transform: translateX(-750rpx);
				}

				.product-hide {
					transform: translateX(750rpx);
				}
			}

		}
	}
</style>
