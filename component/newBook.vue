<template>
	<view class="new-book">
		<view class="book-top">
			<view class="title">{{title}}</view>
			<view class="more">
				{{more}}
				<text :class="url"></text>
			</view>
		</view>
		<view class="book-item" v-for="item in newBookShow">
			<view class="item-box">
				<view class="left">
					<image :src="item.src"></image>
				</view>
				<view class="right">
					<view class="info-title">{{item.infoTitle}}</view>
					<view class="info-content">{{item.infoContent}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data() {
			return{
				title: '新书广场',
				more: '更多',
				url: 'iconfont icon-genduo1',
			}
		},
		props:[
			'newBookShow'
		]
	}
</script>

<style lang="less" scoped>
	.new-book{
		margin: 20rpx;
		.book-top{
			display: flex;
			justify-content: space-between;
			.more,text{
				font-size: 9px;
				color: #999999;
			}
		}
		.book-item{
			.item-box{
				display: flex;
				margin: 20rpx 0;
				
				.left{
					flex: 1;
					image{
						width: 90%;
						height: 200rpx;
					}
				}
				.right{
					flex: 2;
					overflow: hidden;//父选择器需要加这个属性，否则会溢出
					.info-title{
						width: 95%;
						font-size: 28rpx;
						//溢出文本显示省略号
						text-overflow: ellipsis;
						white-space: nowrap;
						overflow: hidden;
					}
					.info-content{
						font-size: 24rpx;
						color: #999999;
						padding-top: 20rpx;
						width: 95%;
						display: -webkit-box;
						//多行文本溢出显示省略号
						-webkit-box-orient: vertical;    
						-webkit-line-clamp: 3;    
						overflow: hidden;
					}
				}
			}
		}
	}
</style>
