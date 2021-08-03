<template>
	<view class="book-rec">
		<view class="book-top">
			<view class="title">{{title}}</view>
			<view class="more">
				{{more}}
				<text :class="icon"></text>
			</view>
		</view>
		<scroll-view scroll-x="true" >
			<view class="book-content">
				<view class="book-item"  v-for="item in bookInfo">
					<image :src="item.img"></image>
					<view class="book-info">
						<view class="title">{{item.title}}</view>
						<view class="writer">作者：{{item.writer}}</view>
						<view class="shop-style">
							方式：<text>{{item.style}}</text>
						</view>
					</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default{
		data() {
			return {
				title: '好书推荐',
				more: '更多',
				icon: 'iconfont icon-genduo1'
			}
		},
		props:[
			'bookInfo'
		]
	}
</script>

<style lang="less" scoped>
	.book-rec{
		.book-top{
			padding: 20rpx;
			display: flex;
			justify-content: space-between;
			.more,text{
				font-size: 24rpx;
				color: #999999;
			}
		}
		.book-content{
			display: flex;
			overflow-x: auto;
			margin: 0 20rpx;
			.book-item:nth-child(n+2){
				margin-left: 25rpx;
			}
			.book-item{
				flex: none;
				width: 200rpx;
				// background-color: #CCC;
				image{
					width: 90%;
					height: 200rpx;
					margin: 5%;
				}
				.book-info{
					padding: 20rpx 0;
					.title{
						font-size: 20rpx;
					}
					.writer{
						font-size: 18rpx;
						color: #999999;
						padding: 10rpx 0;
					}
					.shop-style{
						font-size: 18rpx;
						text{
							font-size: 24rpx;
							font-weight: 600;
							color: #DD524D;
						}
					}
				}
			}
		}
	}
</style>
