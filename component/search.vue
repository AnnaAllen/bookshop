<template>
	<view class="search">
		<slot name="left"></slot>
		<view class="search-in">
			<input 
			type="text" 
			:placeholder='message'
			confirm-type="搜索"
			@confirm="inputData"
			><!-- @confirm="inputData"：回车后把执行这个方法 -->
			<text class="iconfont icon-xingtaiduICON_sousuo--"></text>
		</view>
		<slot name="right"></slot>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				testData: '',
				message: '请输入名称/作者'
			}
		},
		methods:{
			inputData(e){
				this.testData = e.detail.value
				uni.setStorageSync('searchData',this.testData)
				uni.navigateTo({
					url:'../findBook/findBook'
				})
			},
		},
		
	}
</script>

<style lang="less" scoped>
	.search{
		display: flex;
		font-size: 24rpx;
		height: 100rpx;
		vertical-align: center;
		align-items: center;
		.search-in{
			flex: 6;
			border: 1px solid #DD524D;
			border-radius: 10px;
			height: 60rpx;
			padding-left: 8%;
			position: relative;
			input{
				padding-top: 1%;
			}
			text{
				position: absolute;
				top: 19%;
				left: 2%;
				color: #999999;
			}
		}
	}
</style>
