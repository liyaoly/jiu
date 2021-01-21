<template>
	<view class="quotation">
		<!-- 自定义导航区域 -->
		<uni-nav-bar background-color="#ff6666" color="#fff" title="行情中心" :fixed="true" :status-bar="true">
			<!-- 	<view class="searchInput" slot="left">
				<image class="search_icon" src="../../static/search_icon.png"></image>
				<input type="text" placeholder-class="placeholderClass" placeholder="请输入关键字">
			</view> -->
		</uni-nav-bar>
		<!-- 内容区域 -->
		<view class="content">
			<!-- 热门板块 -->
			<view class="hot-box">
				<view class="hot-box-title">
					<view class="hot-box-title-left">
						<image src="../../static/Label.png" mode=""></image>
						<text>热门品牌酒板块</text>
					</view>
					<view class="hot-box-title-right">>
						<!-- <uni-icons type="right"></uni-icons> -->
					</view>
				</view>
				<view class="brandsBox">
					<view v-for="(item,index) in hotList" :key="index" class="itembox" :class="index>2?'orange':''" @click="seeDetail(item)">
						<view class="itemName">{{item.name}}
						</view>
						<view class="itemNumber">
							{{item.price}}
							(
							{{item.status ==='rise'?'+':'-'}}
							{{item.range}}
							)
						</view>
					</view>
				</view>
			</view>
			<!-- 涨跌切换 -->
			<view class="tabar">
				<view class="tabar-item" :class="showTab==='rise'?'tabar-item-active':''" @tap="changeTo('rise')">涨幅榜</view>
				<view class="tabar-item" :class="showTab==='fall'?'tabar-item-active':''" @tap="changeTo('fall')">跌幅榜</view>
			</view>
			<view class="listBox">
				<view class="Riselist" :class="showTab==='rise'?'':'hide1'">
					<view class="aHeader">
						<view>品牌</view>
						<view>最新价</view>
						<view>涨幅</view>
					</view>
					<view class="listBox-scorllbox">
						<view v-for="(item,index) in Riselist" :key="index" class="listBox-scorllbox-item" @tap="navgateTo(item)">
							<view>{{item.name}}</view>
							<view>{{item.price}}</view>
							<view class="rise"><text>+</text><text>{{item.range}}</text></view>
						</view>
					</view>
				</view>
				<view class="Falllist" :class="showTab==='fall'?'':'hide2'">
					<view class="aHeader">
						<view>品牌</view>
						<view>最新价</view>
						<view>跌幅</view>
					</view>
					<view class="listBox-scorllbox">
						<view v-for="(item,index) in falllist" :key="index" class="listBox-scorllbox-item" @tap="navgateTo(item)">
							<view>{{item.name}}</view>
							<view>{{item.price}}</view>
							<view class="fall"><text>-</text><text>{{item.range}}</text></view>
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
				showTab: 'rise',
				hotList: [{
						name: '汾酒',
						price: '2600',
						status: 'rise',
						range: '45%'
					},
					{
						name: '洋河',
						price: '3400',
						status: 'rise',
						range: '42%'
					},
					{
						name: '剑南春',
						price: '6700',
						status: 'rise',
						range: '45%'
					},
					{
						name: '郎酒',
						price: '6700',
						status: 'rise',
						range: '45%'
					},
					{
						name: '贵州喜酒',
						price: '6700',
						status: 'rise',
						range: '45%'
					},
					{
						name: '水井坊',
						price: '6700',
						status: 'rise',
						range: '45%'
					}
				],
				Riselist: [{
						name: '剑南春',
						price: '2345',
						range: '2.45%'
					},
					{
						name: '剑南春',
						price: '2345',
						range: '2.45%'
					},
					{
						name: '剑南春',
						price: '2345',
						range: '2.45%'
					},
					{
						name: '剑南春',
						price: '2345',
						range: '2.45%'
					}
				],
				falllist: [{
						name: '剑南春',
						price: '2345',
						range: '2.45%'
					},
					{
						name: '剑南春',
						price: '2345',
						range: '2.45%'
					},
					{
						name: '剑南春',
						price: '2345',
						range: '2.45%'
					},
					{
						name: '剑南春',
						price: '2345',
						range: '2.45%'
					},
					{
						name: '剑南春',
						price: '2345',
						range: '2.45%'
					},
					{
						name: '剑南春',
						price: '2345',
						range: '2.45%'
					}
				]
			}
		},
		methods: {
			changeTo(type) {
				this.showTab = type
				console.log(type)
			},
			navgateTo(data) {
				uni.navigateTo({
					url: '../quotationChart/quotationChart',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
				console.log(data)
			},
			seeDetail(data) {
				uni.navigateTo({
					url: '../quotationData/quotationData',
					success: res => {},
					fail: () => {},
					complete: () => {}
				})
			}
		}
	}
</script>

<style scoped lang="scss">
	.quotation {
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
			background-color: #eeeeee;

			.hot-box {
				width: 100%;
				height: 426upx;
				background: #FFFFFF;
				box-shadow: 0px 8px 13px 0px rgba(55, 55, 55, 0.09);
				box-sizing: border-box;
				padding: 0 30upx 40upx 30upx;
				margin-bottom: 40upx;

				.hot-box-title {
					width: 100%;
					height: 96upx;
					display: flex;
					justify-content: space-between;
					line-height: 96upx;

					.hot-box-title-left {
						image {
							width: 21upx;
							height: 28upx;
						}

						text {
							font-size: 26upx;
							font-family: SourceHanSansSC;
							font-weight: bold;
							color: #333333;
						}

					}
				}

				.brandsBox {
					display: flex;
					flex-wrap: wrap;
					justify-content: space-between;

					.itembox {
						width: 210upx;
						height: 140upx;
						background: #FF7C66;
						border-radius: 8px;
						text-align: center;
						display: flex;
						flex-direction: column;
						justify-content: center;
						margin-bottom: 20upx;

						.itemName {
							font-size: 26upx;
							font-family: MicrosoftYaHeiUI;
							font-weight: bold;
							color: #FFFFFF;
						}

						.itemNumber {

							font-size: 24upx;
							font-family: MicrosoftYaHeiUI;
							font-weight: 400;
							color: #FFFFFF;
						}
					}

					.orange {
						background-color: #FFB157;
					}
				}
			}

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
				height: auto;
				min-height: 560upx;
				position: relative;
				overflow-x: hidden;
				overflow-y: scroll;
				position: relative;

				.Riselist,
				.Falllist {
					width: 100%;
					height: auto;
					background: #fff;
					position: absolute;
					transition: all 0.5s;

					.aHeader {
						width: 100%;
						height: 80upx;
						background: #EEEEEE;
						display: flex;
						box-sizing: border-box;
						padding: 0 20upx;
						justify-content: space-between;
						font-size: 26upx;
						font-weight: bold;
						color: #333333;
						text-align: center;
						line-height: 80upx;
					}

					.listBox-scorllbox {
						width: 100%;
						background: #fff;
						height: 560upx;
						overflow-y: scroll;
					}

					.listBox-scorllbox-item {
						display: flex;
						justify-content: space-between;
						text-align: center;
						box-sizing: border-box;
						padding: 0 40upx;
						height: 116upx;
						line-height: 116upx;
						border: 1px solid #EEEEEE;
						font-size: 26upx;
						font-family: SourceHanSansSC;
						font-weight: 500;
						color: #666666;

						.status,
						.unit {
							margin-right: 10upx;
							font-size: 20upx;
						}

					}

					.rise {

						color: #FF6666;

					}

					.fall {

						color: #0066CC;

					}
				}
			}

			.hide1 {
				transform: translateX(-750rpx);
			}

			.hide2 {
				transform: translateX(750rpx);
			}
		}

	}
</style>
