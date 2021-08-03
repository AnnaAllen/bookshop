<template>
	<view class="user-like">
		<view class="like-item">
			<view class="item-box2" v-for="item in userCllect">
				<view class="box2-big">
					<view class="box2-user-info">
						<view class="user-img">
							<image :src="item.writerImg"></image>
							<view>{{item.writer}}</view>
						</view>
						<view class="attention" v-if="item.attention" @click="changeAtten(item.writerId)">已收藏</view>
						<view class="attention2" v-else @click="changeAtten(item.writerId)">添加收藏</view>
					</view>
					<view class="box2-title">{{item.title}}</view>
					<view class="box2-content">{{item.content}}</view>
					<view class="box2-img">
						<image :src="item.image"></image>
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
				
			}
		},
		props:[
			'userCllect'
		],
		methods:{
			changeAtten(id){
				this.$emit('getNewAtten',id)//每点击一次就把id传回给parent组件
			}
		}
	}
</script>

<style lang="less" scoped>
	.user-like{
		.like-item{
			.item-box2{
				padding: 10rpx 20rpx;
				.box2-big{
					padding-bottom: 20rpx;
					border-bottom: 2rpx solid #F1F1F1;
					.box2-user-info{
						display: flex;
						height: 7vh;
						// background-color: pink;
						align-items: center;
						justify-content: space-between;
						font-size: 24rpx;
						.user-img{
							display: flex;
							align-items: center;
							image{
								height: 60rpx;
								width: 60rpx;
								border-radius: 30rpx;
							}
							view{
								margin-left: 20rpx;
							}
						}
						.attention{
							background-color: #C8C7CC;
							padding: 10rpx 20rpx;
							border-radius: 20rpx;
							color: white;
						}
						.attention2{
							background-color: #F0AD4E;
							padding: 10rpx 20rpx;
							border-radius: 20rpx;
							color: white;
						}
					}
					.box2-title{
						width: 85%;
						font-weight: 600;
						font-size: 28rpx;
						padding: 10rpx;
						text-overflow: ellipsis;
						white-space: nowrap;
						overflow: hidden;
					}
					.box2-content{
						padding: 10rpx;
						color: #555555;
						font-size: 24rpx;
						//多行文本溢出显示省略号
						display: -webkit-box;
						-webkit-box-orient: vertical;    
						-webkit-line-clamp: 3;    
						overflow: hidden;
					}
					.box2-img{
						image{
							width: 100%;
							border-radius: 10rpx;
						}
					}
				}
			}
		}
	}
</style>
