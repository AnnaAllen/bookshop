<template>
	<view class="public">
		<view class="public-box">
			<uni-transition modeClass="slide-bottom" :show="show" :duration="time">
				<view class="public-item" v-for="(item,index) in publicItem">
					<view class="blank"></view>
					<view class="item-img" @click="jumpTo(index)">
						<view :class="item.icon"></view>
					</view>
					<view class="item-content" @click="jumpTo(index)">
						<view class="title">{{item.title}}</view>
						<view class="explain">{{item.content}}</view>
					</view>
				</view>
			</uni-transition>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				publicItem: [
					{
						'icon': 'iconfont icon-jiaohuan',
						'title': '以书易书',
						'content': '用书籍跟其他人交换书籍'
					},
					{
						'icon': 'iconfont icon-yiwu',
						'title': '以书易物',
						'content': '用书籍跟其他人交换物品'
					},
					{
						'icon': 'iconfont icon-chushou',
						'title': '出售图书',
						'content': '出售闲置的二手图书'
					},
					{
						'icon': 'iconfont icon-jiaoliu',
						'title': '书评聊天',
						'content': '发布自己的感想与他人交流'
					}
				],
				show: false,
				time: 700,
			}
		},
		methods: {
			open(mode) {
			  this.show = true
			},
			changeShow(){
				this.show = false
			},
			jumpTo(index){
				uni.setStorageSync('publishData',this.publicItem[index].title)
				uni.navigateTo({
					url:'../publishPage/publishPage'
				})
			}
		},
		onShow() {
			this.open()
		},
		onHide() {
			this.changeShow()
		}
	}
</script>

<style lang="less" scoped>
	.public{
		position: relative;
		background-color: #555555;
		height: 100vh;
		.public-box{
			position: absolute;
			left: 0;
			right: 0;
			top: 15vh;
			.public-item{
				display: flex;
				// background-color: pink;
				justify-content: center;
				align-items: center;
				height: 10vh;
				padding: 4% 0;
				// box-shadow: 0 1rpx 10rpx #FFFFFF;
				.blank{
					flex: 1;
				}
				.item-img{
					flex: 1;
					view{
						height: 100rpx;
						width: 100rpx;
						background-color: #DD524D;
						border-radius: 50rpx;
						text-align: center;
						line-height: 100rpx;
						color: white;
						font-size: 70rpx;
						// float: right;
					}
				}
				.item-content{
					flex: 3;
					// border-bottom: 2rpx solid #C8C7CC;
					.title{
						font-weight: 600;
						padding-bottom: 1%;
						color: white;
					}
					.explain{
						color: #999999;
						font-size: 28rpx;
					}
				}
			}
		}
	}
</style>
