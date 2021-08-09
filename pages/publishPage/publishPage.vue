<template>
	<view class="publish-page">
		<view class="pubilsh">
			<view class="title">
				<input type="text" placeholder="标题 ( 可选 )" @blur="titleFinsh">
			</view>
			<view class="content">
				<textarea 
				placeholder="内容" 
				maxlength="-1" 
				auto-height="true" 
				@blur="textFinsh"
				/>
			</view>
			<view class="picture">
				<!-- 预览图片 -->
				<view  class="look-img">
					<image v-for="item in userInputInfo.updataImg" :src="item" @click="previewImg(item)" :key="item"></image>
					<!-- 上传图片 -->
					<view class="pictureShow" @click="updata" >
						<view>+上传图片</view>
					</view>
				</view>
								
				<view class="continue" @click="pubilshItem">
					<view>发布{{pubilshStyle}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo: {
					'name': 'Anna',
					'img': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg'
				},
				pubilshStyle: '',
				userInputInfo:{
					'updataImg': [],
					'title':'',
					'content':''
				}
			}
		},
		methods: {
			updata(){
				uni.chooseImage({
					count:9,
					success: res=>{
											this.userInputInfo.updataImg = res.tempFilePaths
										},
				})
				
			},
			previewImg(item){
				 uni.previewImage({
				    urls: this.userInputInfo.updataImg,
				    current
				  })
					
			},
			//获取用户输入的标题
			titleFinsh(e){
				this.userInputInfo.title = e.detail.value
			},
			//获取用户输入的内容
			textFinsh(e){
				this.userInputInfo.content = e.detail.value
			},
			//用户点击发布后
			pubilshItem(){
				uni.setStorageSync('userInputInfo',this.userInputInfo)
			}
		},
		onShow(){
			this.pubilshStyle = uni.getStorageSync('publishData')
		}
	}
</script>

<style lang="less" scoped>
	.publish-page{
		.pubilsh{
			padding: 20rpx;
			.title{
				input{
					border-bottom: 1rpx solid #C8C7CC;
					height: 60rpx;
					padding-left: 20rpx;
				}
			}
			.content{
				textarea{
					padding: 20rpx;
				}
			}
			.picture{
				.look-img{
					display: flex;
					flex-wrap: wrap;
					// justify-content: space-around;
					image{
						// flex: 1;
						width: 32%;
						height: 200rpx;
						border-radius: 10rpx;
						margin: 20rpx 0;
					}
					image:nth-child(2){
						margin: 20rpx calc(~ " 4% - 20rpx ");
					}
					image:nth-child(5){
						margin: 20rpx calc(~ " 4% - 20rpx ");
					}
					image:nth-child(8){
						margin: 20rpx calc(~ " 4% - 20rpx ");
					}
				}
				
				.pictureShow{
					width: 32%;
					height: 200rpx;
					background-color: #F1F1F1;
					color: #999999;
					font-size: 28rpx;
					text-align: center;
					line-height: 200rpx;
					display: block;
					margin: 20rpx 0 20rpx 1%;
				}
				.continue{
					padding: 30rpx 20rpx;
					text-align: center;
					view{
						background-color: #DD524D;
						padding: 10rpx;
						border-radius: 10rpx;
						color: white;
						letter-spacing: 2rpx;
					}
				}
			}
		}
	}
</style>
