<template>
	<view class="classiy">
		<view class="classiy-item">
			<view  v-for="(item,index) in name" class="classiy-style">
				<text :class='item.img' @click="jump(index)"></text>
				<view>{{item.name}}</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		props:[
			'name'
		],
		methods:{
			jump(num){
				console.log(this.name[num].url)
				uni.setStorageSync('classify',num)
				uni.switchTab({
					url:this.name[num].url
				})
			}
		}
	}
</script>

<style lang="less" scoped>
	.classiy{
		.classiy-item{
			display: flex;
			.classiy-style{
				flex: 1;
				text-align: center;
				font-size: 24rpx;
				text{
					color: white;
					font-size: 60rpx;
					background-color: #DD524D;
					border-radius: 50rpx;
					padding: 10rpx;
				}
				view{
					padding-top: 20rpx;
				}
			}
		}
	}
</style>
