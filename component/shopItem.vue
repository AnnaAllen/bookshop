<template>
	<view class="shop-item">
		<view class="item-box" v-for="(item,index) in userInfo" >
			<view @click="jumpTo(index)">
				<view class="img-box">
					<image :src="item.userP" mode="widthFix"></image>
				</view>
				<view class="content">{{item.userContent}}</view>
			</view>
			<view class="user-box">
				<view class="user-img">
					<image :src="item.userImg" mode="aspectFill"></image>
				</view>
				<view class="user-name">{{item.userName}}</view>
				<view 
				class="user-like" 
				:class="{islike: item.isLike}"
				@click="like(item.userID)"
				>
					<text class="iconfont icon-home_ico_like-" ></text>
					{{item.userLike}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data() {
			return{
				isLike: false,
			}
		},
		props:[
			'userInfo'
		],
		methods:{
			like(userID){
				this.$emit('changeUserLike',userID)
			},
			jumpTo(index){
				uni.navigateTo({
					url:"../bookInfoDetail/bookInfoDetail"
				})
			}
		},
		//页面初次渲染完成后加载
		mounted() {
		}
	}
</script>

<style lang="less" scoped>
	.islike{
		color: #DD524D;
	}
	.shop-item{
		// padding: 20rpx;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		.item-box{
			width: 48.3%;
			overflow: hidden;
			margin-bottom: 20rpx;
			.img-box{
				image{
					width: 100%;
					border-radius: 20rpx;
				}
			}
			.content{
				font-size: 28rpx;
				letter-spacing: 2rpx;
				//多行文本溢出省略号
				display: -webkit-box;
				-webkit-box-orient: vertical;
				-webkit-line-clamp: 2;    
				overflow: hidden;
			}
			.user-box{
				padding: 20rpx 0;
				line-height: 60rpx;
				height: 60rpx;
				// background-color: pink;
				font-size: 24rpx;
				color: #999999;
				display: flex;
				.user-img{
					flex: 1;
					padding-right: 10rpx;
					image{
						width: 90%;
						height: 90%;
						border-radius: 50rpx;
					}
				}
				.user-name{
					flex: 3;
					text-overflow: ellipsis;
					white-space: nowrap;
					overflow: hidden;
				}
				.user-like{
					flex: 1;
					text{
						font-size: 24rpx;
						padding-right: 10rpx;
					}
				}
			}
		}
	}
</style>
