<template>
	<view class="user-info">
		<view class="item">
			<view class="img">
				<image :src="userInfo.userImg"></image>
			</view>
			<view class="user-name">
				<view class="user-title">{{userInfo.userName}}</view>
				<view class="user-id">会员ID：{{userInfo.userId}}</view>
			</view>
		</view>
		<view class="icon">
			<view class="iconfont icon-genduo1"></view>
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
			'userInfo'
		]
	}
</script>

<style scoped lang="less">
	.user-info{
		display: flex;
		justify-content: space-between;
		align-items: center;
		.item{
			display: flex;
			align-items: center;
			height: 10vh;
			// background-color: pink;
			.img{
				image{
					width: 120rpx;
					height: 120rpx;
					border-radius: 50%;
				}
			}
			.user-name{
				padding-left: 20rpx;
				.user-id{
					color: #999999;
					font-size: 24rpx;
				}
			}
		}
		.icon{
			color: #999999;
		}
	}
</style>
