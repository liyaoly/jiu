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
				<view class="brand-item" v-for="(item,index) in brand" :key="index">
					<view class="left info">
						<view class=""><text class="brandName">{{item.name}}</text><icon :type="item.status" size="26"/></view>
						<view class=""><text class="typeLabel">品牌</text><text class="focusTime">{{item.time}}</text></view>
						<view class="range">{{item.range}}</view>
					</view>
					<view class="right info">
						<text class="unit">￥</text>
						<text class="price">{{item.price}}</text>
					</view>
					
				</view>
			</view>
			<view class="product" :class="showTab==='product'?'':'product-hide'">
				<view class="brand-item" v-for="(item,index) in product" :key="index">
					<view class="left info">
						<view class=""><text class="brandName">{{item.name}}</text><icon :type="item.status" size="26"/></view>
						<view class=""><text class="typeLabel">品牌</text><text class="focusTime">{{item.time}}</text></view>
						<view class="range">{{item.range}}</view>
					</view>
					<view class="right info">
						<text class="unit">￥</text>
						<text class="price">{{item.price}}</text>
					</view>
					
				</view>
			</view>
			</view>
			
		</view>

	</view>
</template>

<script>
	export default{
		data(){
			return {
				showTab:'brand',
				brand:[
					{
						name:'古井贡酒',
						time:'12天前关注',
						status:'top',
						range:'40%',
						price:5978
					},
					{
						name:'贵州茅台',
						time:'12天前关注',
						status:'up',
						range:'40%',
						price:1299
					},
					{
						name:'古井贡酒',
						time:'12天前关注',
						status:'top',
						range:'40%',
						price:5978
					},
					{
						name:'贵州茅台',
						time:'12天前关注',
						status:'up',
						range:'40%',
						price:1299
					},
					{
						name:'古井贡酒',
						time:'12天前关注',
						status:'top',
						range:'40%',
						price:5978
					},
					{
						name:'贵州茅台',
						time:'12天前关注',
						status:'up',
						range:'40%',
						price:1299
					}
				],
				product:[
					{
						name:'古井贡酒',
						time:'12天前关注',
						status:'top',
						range:'40%',
						price:5978
					},
				]
				
			}
		},
		methods:{
			changeTo(type){
				this.showTab = type
				console.log(type)
			},
			onClickLeft(e){
				uni.navigateBack({
					delta: 1
				});
				
			}
		}
	}
</script>

<style scoped lang="scss">
	.myFocus{
		.content{
			background: #EEEEEE;
			.tabar{
				width: 750upx;
				height: 100upx;
				background: #FFFFFF;
				display: flex;
				text-align: center;
				justify-content: space-between;
				line-height: 100upx;
				.tabar-item{
					flex: 1;
					font-size: 30upx;
					font-family: SourceHanSansSC;
					font-weight: 400;
					color: #666666;
				}
				.tabar-item-active{
					border-bottom:2px solid #0066CC;
					font-weight: bold;
					color: #0066CC;
				}
				

			}
			.listBox{
				width: 100%;
				height: auto;
				min-height: 1106upx;
				position: relative;
				overflow-x: hidden;
				overflow-y: scroll;
				position: relative;
				.brand,.product{
					width: 100%;
					height: auto;
					box-sizing: border-box;
					padding: 20upx;
					background: #EEEEEE;
					position: absolute;
					transform: translateX(0);
					transition: all 0.5s;
					.brand-item{
						width: 670upx;
						height: 218upx;
						background: #FFFFFF;
						border-radius: 8upx;
						display: flex;
						margin: 20upx;
						justify-content: space-between;
						box-sizing: border-box;
						padding: 40upx 60upx;
						
						.left{
							display: flex;
							flex-direction: column;
							justify-content: space-between;
						}
						.right{
							display: flex;
							flex-direction: row;
							justify-content: center;
							align-items: center;
							text-align: center;
							
						}
						.info{
							flex: 1;
							height: 100%;
							
							
							.brandName{
							
								font-size: 36upx;
								font-family: SourceHanSansSC;
								font-weight: bold;
								color: #333333;
				
							}
							.typeLabel{
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
							.focusTime{
								font-size: 20upx;
								color: #666666;
				
							}
							.range{
								
								font-size: 26upx;
								font-weight: bold;
								color: #FF6666;
				
							}
							.unit{
								font-size: 20upx;
								font-weight: bold;
								color: #FFFFFF;
								text-shadow: -1px 0px 2px #4D1D1D;
							}
							.price{
								
								font-size: 30upx;
								font-weight: bold;
								color: #FFFFFF;
								text-shadow: -1px 0px 2px #4D1D1D;
							}
						}
				
					}
				}
				.brand-hide{
					transform: translateX(-750rpx);
				}
				.product-hide{
					transform: translateX(750rpx);
				}
			}
			
		}
	}
	
</style>
