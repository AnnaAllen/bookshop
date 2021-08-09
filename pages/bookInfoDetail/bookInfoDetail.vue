<template>
	<view class="book-info-detail">
		<view class="writer-info">
			<view class="img-box">
				<image :src="bookInfo.writerImg"></image>
			</view>
			<view class="name">
				<view>{{bookInfo.writer}}</view>
				<view>ID：{{bookInfo.writerId}}</view>
			</view>
			<view 
			class="collect2" 
			v-if="bookInfo.attention"
			@click="change"
			><text>已收藏</text></view>
			<view 
			class="collect" 
			v-else
			@click="change"
			><text>+收藏</text></view>
		</view>
		<view class="book-style">
			<text>{{bookInfo.bookStyle}}</text>
			<text v-if="bookInfo.price"> ￥{{bookInfo.price}}</text>
		</view>
		<view class="white-content">
			<view class="content-title">{{bookInfo.title}}</view>
			<view class="content-text">{{bookInfo.content}}</view>
			<view class="content-img">
				<!-- 书评则展示轮播图 -->
				<view v-if="isSwiper">
					<swiper indicator-dots="true">
						<swiper-item>
							<image :src="bookInfo.image"></image>
							</swiper-item>
						</swiper>
				</view>
				<!-- 不是书评就直接展示图片 -->
				<view v-else>
					<image :src="bookInfo.image" mode="widthFix"></image>
				</view>
			</view>
		</view>
		<view class="leave-a-message">
			<view class="message-box1">
				<view>全部留言·{{commentInfo.length}}</view>
				<view>{{num}}次收藏</view>
			</view>
			<view class="comment">
				<view class="userImg"><image :src="bookInfo.image"></image></view>
				<view class="input-box"><input type="text"></view>
			</view>
			<view class="comment-info" v-for="item in commentInfo">
				<view class="comment-userimg">
					<image :src="item.img"></image>
				</view>
				<view class="comment-userinfo">
					<view class="comment-user">
						<view class="c-name"><text>{{item.name}}</text></view>
						<view class="c-reply" v-if="item.reply">>>回复：{{item.reply}}</view>
					</view>
					<view class="comment-content-info">{{item.content}}</view>
					<view class="comment-content-time">{{item.time}}</view>
				</view>
			</view>
		</view>
		<view class="recommend-book">
			<view class="recommend-title">———{{recommendTitle}}———</view>
			<shop-item></shop-item>
		</view>
		<view class="fixed-box">
			<view class="contact">
				<view class="like">
					<text class="iconfont icon-xihuan" :class="{isLike:bookInfo.attention}"></text>
					<text>{{num}}次喜欢</text>
				</view>
				<view class="I-Want"><text>{{iWant}}</text></view>
			</view>
		</view>
	</view>
</template>

<script>
	import shopItem from '../../component/shopItem.vue'
	export default {
		data() {
			return {
				bookInfo: {},
				isSwiper: false,
				price: null,
				num: 5,
				iWant: '我想要',
				recommendTitle: '为你推荐',
				commentInfo: [
					{
						'name':'yagami Light',
						'img': 'https://www.z4a.net/images/2021/08/06/16282397321.png',
						'content': '我想买这本书',
						'reply': null,
						'time': '2021-10-20'
					},
					{
						'name':'yagami Light',
						'img': 'https://www.z4a.net/images/2021/08/06/16282397321.png',
						'content': '我想买这本书',
						'reply': 'L',
						'time': '2021-10-20'
					}
				]
			}
		},
		methods: {
			getBookData(){
				this.bookInfo = uni.getStorageSync('bookDetail')
			},
			change(){
				this.bookInfo.attention = !this.bookInfo.attention
			},
			changValue(){
				// 书评
				if(this.bookInfo.bookStyleNum == 3){
					 this.isSwiper = true
				}else{
					 this.isSwiper = false
				}
				//出售图书时，显示交易额
				this.price = this.bookInfo.price
			}
		},
		components:{
			shopItem
		},
		onShow() {
			this.getBookData()
			this.changValue()
		}
	}
</script>

<style scoped lang="less">
	.isLike{
		color: #DD524D;
	}
	.book-info-detail{
		.writer-info{
			padding: 20rpx;
			margin-bottom: 10rpx;
			display: flex;
			align-items: center;
			height: 100rpx;
			// background-color: pink;
			.img-box{
				flex: 1;
				image{
					width: 90rpx;
					height: 90rpx;
					border-radius: 50%;
				}
			}
			.name{
				padding-left: 20rpx;
				font-size: 28rpx;
				flex: 7;
				view:nth-child(2){
					color: #999999;
					font-size: 28rpx;
				}
			}
			.collect{
				letter-spacing: 2rpx;
				flex: 2;
				text{
					float: right;
					font-size: 28rpx;
					background-color: #F0AD4E;
					padding: 15rpx;
					border-radius: 25rpx;
					color: white;
				}
			}
			.collect2{
				flex: 2;
				text{
					float: right;
					font-size: 28rpx;
					background-color: #999999;
					padding: 15rpx;
					border-radius: 25rpx;
					color: white;
				}
			}
		}
		.white-content{
			// border-bottom: 2rpx solid #F1F1F1;
			padding: 20rpx;
			.content-title{
				font-weight: 600;
				padding-bottom: 20rpx;
			}
			.content-img{
				text-align: center;
				image{
					width: 100%;
					// height: 100%;
					// border-radius: 20rpx;
				}
			}
			.content-text{
				padding: 20rpx 0;
				font-size: 28rpx;
			}
		}
		.book-style{
			padding: 20rpx;
			font-size: 30rpx;
			letter-spacing: 2rpx;
			border-bottom: 1rpx solid #F1F1F1;
			margin-bottom: 20rpx;
			text{
				padding: 10rpx;
				border-radius: 20rpx;
				color: #DD524D;
				font-weight: 600;
				background-color: #F1F1F1;
			}
			text:nth-child(2){
				margin-left: 20rpx;
			}
		}
		.leave-a-message{
			border-top: 20rpx solid #F1F1F1;
			padding: 20rpx;
			.message-box1{
				padding: 20rpx 0;
				display: flex;
				justify-content: space-between;
				align-items: center;
				view:nth-child(2){
					color: #999999;
					font-size: 28rpx;
				}
			}
			.comment{
				display: flex;
				align-items: center;
				vertical-align: center;
				padding-bottom: 20rpx;
				border-bottom: 2rpx solid #F1F1F1;
				.userImg{
					flex: 1;
					image{
						width: 60rpx;
						height: 60rpx;
						border-radius: 50%;
					}
				}
				.input-box{
					flex: 8;
					input{
						border: 1rpx solid #999999;
						border-radius: 50rpx;
						background-color: #F1F1F1;
					}
				}
			}
		}
		.comment-info{
			padding: 30rpx 20rpx 20rpx 20rpx;
			border-bottom: 2rpx solid #F1F1F1;
			display: flex;
			.comment-userimg{
				flex: 1;
				image{
					width: 60rpx;
					height: 60rpx;
					border-radius: 50%;
				}
			}
			.comment-userinfo{
				flex: 8;
				padding-left: 20rpx;
				.comment-user{
					padding-bottom: 10rpx;
					display: flex;
					.c-name{
						text{
							padding-right: 20rpx;
							
						}
					}
					.c-reply{
						color: #999999;
						font-size: 28rpx;
					}
				}
				.comment-content-info{
					font-weight: 200;
					padding-bottom: 10rpx;
				}
				.comment-content-time{
					font-size: 24rpx;
					color: #999999;
				}
			}
		}
		.recommend-book{
			padding: 20rpx;
			.recommend-title{
				padding: 20rpx 0;
				color: #DD524D;
				text-align: center;
			}
		}
		.fixed-box{
			background-color: white;
			z-index: 20;
			position: fixed;
			width: 100%;
			height: 90rpx;
			bottom: 0;
			box-shadow: 0 5rpx 10rpx 10rpx #F1F1F1;
		}
		.contact{
			display: flex;
			justify-content: space-between;
			line-height: 90rpx;
			padding: 0 20rpx;
			letter-spacing: 2rpx;
			.like{
				color: #555555;
				text:nth-child(2){
					padding-left: 10rpx;
					color: #999999;
				}
			}
			.I-Want{
				text{
					background-color: #DD524D;
					padding: 10rpx;
					border-radius: 30rpx;
					color: white;
				}
			}
		}
	}
</style>
