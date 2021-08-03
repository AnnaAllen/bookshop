<template>
	<view class="fourth">
		<view class="fourth-item" v-for="item in fourthData">
			<view class="left-item">
				<view class="title">{{item.title}}</view>
				<view class="subhead">{{item.subhead}}</view>
			</view>
			<view class="right-item">
				<image :src="item.url"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{

			}
		},
		props:[
			'fourthData'
		]
	}
</script>

<style lang="less" scoped>
	.fourth{
		display: flex;
		padding: 30rpx 20rpx;
		flex-wrap: wrap;
		view:nth-child(odd) {
			margin-right: 9rpx;
		}
		view:nth-child(n+3){
			margin-top: 10rpx;
		}
		.fourth-item{
			display: flex;
			height: 100rpx;
			width: 49.3%;
			background-color: #F1F1F1;
			border-radius: 10rpx;
			overflow: hidden;
			.left-item{
				flex: 3;
				text-align: left;
				vertical-align: center;
				align-items: center;
				letter-spacing: 2px;
				padding: 14rpx 0 14rpx 24rpx;
				.title{
					font-weight: 600;
					font-size: 28rpx;
					color: #555555;
					margin-bottom: 2rpx;
				}
				.subhead{
					font-size: 24rpx;
					color: #999999;
				}
			}
			.right-item{
				flex: 2;
				background-color: #CCC;
				image{
					width: 100%;
					height: 100%;
					border-radius: 10rpx;
				}
			}
		}
	}
</style>
