<template>
	<view class="search">
		<slot name="left"></slot>
		<view class="search-in">
			<input 
			type="text" 
			placeholder="请输入名称/作者" 
			confirm-type="搜索"
			@confirm="inputData"
			>
			<text class="iconfont icon-xingtaiduICON_sousuo--"></text>
		</view>
		<slot name="right"></slot>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				testData: ''
			}
		},
		methods:{
			inputData(e){
				this.testData = e.detail.value
				this.$emit('userSearch',this.testData)
			}
		}
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
