<template>
	<view class="userCenter">
		<uni-nav-bar background-color="#ff6666" title="个人中心"  color='#fff' :fixed="true" :status-bar="true"></uni-nav-bar>
		<view class="content">
			<view class="top"></view>
			<view class="card">
				<view class="aHeader">
					<image src="../../static/logo.png" mode=""></image>
				</view>
				<view class="aboutMe">
					<view class="box" @tap="navigateTo('../myFocus/myFocus')">
						<view class="number">{{aboutMe.focus}}</view>
						<view class="text">我的关注</view>
					</view>
					<view class="box" @tap="navigateTo('../myStep/myStep')">
						<view class="number">{{aboutMe.step}}</view>
						<view class="text">浏览足迹</view>
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
				aboutMe:{
					focus:4,
					step:16
				}
			}
		},
		methods:{
			navigateTo(url){
				console.log(url)
				uni.navigateTo({
					url: url,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		}
	}
</script>

<style scoped lang="scss">
	.userCenter{
		.content{
			.top{
				width: 750upx;
				height: 300upx;
				background: #FF6666;
			}
			.card{
				width: 670upx;
				height: 300upx;
				background: #FFFFFF;
				box-shadow: 0px 8px 13px 0px rgba(43, 16, 16, 0.38);
				border-radius: 8px;
				position: relative;
				left: 40upx;
				top: -150upx;
				.aHeader{
					width: 160upx;
					height: 160upx;
					border-radius: 50%;
					position: absolute;
					left: 255upx;
					top: -80upx;
					overflow: hidden;
					border: 3px solid #fff;
					image {
						width: 160upx;
						height: 160upx;
					}
				}
				.aboutMe{
					width: 100%;
					height: 212upx;
					position: absolute;
					bottom: 0;
					display: flex;
					.box{
						flex: 1;
						display: flex;
						flex-direction: column;
						justify-content: center;
						text-align: center;
						.number{
							font-size: 48upx;
							font-family: MicrosoftYaHeiUI;
							font-weight: bold;
							color: #333333;
						}
						.text{
							
							font-size: 26upx;
							font-family: SourceHanSansSC;
							font-weight: 400;
							color: #333333;
						}
					}
				}

			}
		}
	}
</style>
