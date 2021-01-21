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
			<view class="tabar">
				<view class="tabar-item" :class="showTab==='week'?'tabar-item-active':''" @tap="changeTo('week')">近7天</view>
				<view class="tabar-item" :class="showTab==='mouth'?'tabar-item-active':''" @tap="changeTo('mouth')">近30天</view>
				<view class="tabar-item" :class="showTab==='quarter'?'tabar-item-active':''" @tap="changeTo('quarter')">近90天</view>
				<view class="tabar-item" :class="showTab==='year'?'tabar-item-active':''" @tap="changeTo('year')">近半年</view>
			</view>
			<view class="chartBox">
				<view class="week">
					<view class="qiun-columns">
						<view class="qiun-charts">
							<canvas canvas-id="canvasLineA" id="canvasLineA" class="charts" @touchstart="touchLineA"></canvas>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uCharts from '../../components/u-charts/u-charts.js';
	// 定义全局变量
	var _self;
	var canvaLineA = null;
	export default {
		data() {
			return {
				// total
				money: 15200,
				num_val: 900,
				percent_val: 60.09,
				
				showTab: 'week',
				cWidth: '',
				cHeight: '',
				pixelRatio: 1,
			}
		},
		// 页面加载执行的函数
		onLoad() {
			_self = this;
			// uni.upx2px(750) 这是uni-app自带的自适应，以750的尺寸为基准。动态变化
			this.cWidth = uni.upx2px(750);
			this.cHeight = uni.upx2px(500);
			this.getServerData(0);
		},
		methods: {
			changeTo(type) {
				this.showTab = type;
				if (type === 'week') {
					this.getServerData(0);
				} else if (type === 'mouth') {
					this.getServerData(1);
				}
			},
			onClickLeft(e) {
				uni.navigateBack({
					delta: 1
				});

			},
			// 获取数据，发请求
			getServerData(index) {
				uni.request({
					// 请求地址
					url: 'https://www.ucharts.cn/data.json',
					// 请求参数
					data: {},
					// 请求成功的回调函数
					success: function(res) {
						console.log(res.data.data.LineA, res.data.data.LineA.categories)
						let LineA = {
							categories: [],
							series: []
						};
						LineA.categories = res.data.data.LineA.categories;
						LineA.series = [res.data.data.LineA.series[index]];
						console.log(LineA.series)
						// 找到id为canvasLineA的块
						_self.showLineA("canvasLineA", LineA);
					},
					// 请求失败的回调函数
					fail: () => {
						_self.tips = "网络错误，小程序端请检查合法域名";
					},
				});
			},
			// 展示图标的函数 接收参数，一个块的id,一个数据
			showLineA(canvasId, chartData) {
				canvaLineA = new uCharts({
					$this: _self,
					canvasId: canvasId,
					// 图标类型
					type: 'line',
					fontSize: 11,
					legend: {
						show: true
					},
					dataLabel: false,
					dataPointShape: true,
					background: '#FFFFFF',
					pixelRatio: _self.pixelRatio,
					categories: chartData.categories,
					series: chartData.series,
					animation: true,
					// x轴显示的内容
					xAxis: {
						type: 'grid',
						gridColor: '#CCCCCC',
						gridType: 'solid',
						// dashLength:8,
						disableGrid: true,
					},
					// y轴显示的内容
					yAxis: {
						type: 'grid',
						gridColor: '#CCCCCC',
						gridType: 'solid',
						disabled: false,
						// splitNumber:5,
						// min:10,
						// max:180,
						format: (val) => {
							return val.toFixed(0) + '元'
						}
					},
					width: _self.cWidth * _self.pixelRatio,
					height: _self.cHeight * _self.pixelRatio,
					extra: {
						line: {
							type: 'straight'
						}
					}
				});

			},
			// 点击图表显示的内容
			touchLineA(e) {
				// 使用声明的变量canvaLineA
				canvaLineA.showToolTip(e, {
					format: function(item, category) {
						return category + ' ' + item.name + ':' + item.data
					}
				});
			}
		}
	}
</script>

<style scoped lang="scss">
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

		.chartBox {
			width: 100%;
			height: auto;
			min-height: 956upx;
			position: relative;
			overflow-x: hidden;
			overflow-y: scroll;
			position: relative;

			/*样式的width和height一定要与定义的cWidth和cHeight相对应*/
			.qiun-charts {
				width: 713upx;
				height: 658upx;
				margin: 0 auto;
				background-color: #FFFFFF;
			}

			.charts {
				width: 750upx;
				height: 500upx;
				background-color: #FFFFFF;
			}
		}
	}
</style>
