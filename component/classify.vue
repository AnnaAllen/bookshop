<template>
	<view class="classiy">
		<view class="classiy-item">
			<view  v-for="item in name" class="classiy-style">
				<text :class='item.img'></text>
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
		]
	}
</script>

<style lang="less" scoped>
	.classiy{
		.classiy-item{
			display: flex;
			.classiy-style{
				flex: 1;
				text-align: center;
				font-size: 18rpx;
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
