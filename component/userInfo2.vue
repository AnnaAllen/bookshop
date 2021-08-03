<template>
	<view class="user-message">
		<view class="item-num">
			<view v-for="item in num">{{item}}</view>
		</view>
		<view class="item" >
			<view class="goods" v-for="item in goods">{{item}}</view>
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
			'num',
			'goods'
		]
	}
</script>

<style scoped lang="less">
	.user-message{
		.item-num{
			display: flex;
			text-align: center;
			view{
				flex: 1;
			}
		}
		.item{
			display: flex;
			align-items: center;
			text-align: center;
			.goods{
				font-size: 30rpx;
				flex: 1;
			}
		}
	}
</style>
