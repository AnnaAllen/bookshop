<template>
	<view class="big-box">
		<view class="searchPage">
			<search @userSearch="userSearch"></search>
			<view class="search-history">
				<view class="title">
					<view class="title-box">历史搜索记录</view>
					<view class="icon-box">
						<view class="iconfont icon-qingchu" @click="deleteData"></view>
					</view>
				</view>
			</view>
			<view class="history-box">
				<view v-if="historyData" class="hasHistory">
					<view class="history-item" v-for="item in historyData">
						{{item}}
					</view>
				</view>
				<view v-else class="forAWhite">暂无搜索记录</view>
			</view>
		</view>
	</view>
</template>

<script>
	import search from "../../component/search.vue"
	export default {
		data() {
			return {
				useInput: [],
				historyData: ['水','火','L月','黑色小本本','夜神月','misa','L','deathNote']
			}
		},
		methods: {
			deleteData(){
				this.historyData = null
			},
			userSearch(str){
				this.historyData.push(str)
				//跳转到寻书的推荐页面
				uni.switchTab({
					url:'../find/find'
				})
				//把参数设置到缓存中
				uni.setStorageSync('searchData',str)
			}
		},
		
		components:{
			search
		},
	}
</script>

<style scoped lang="less">
	.searchPage{
		padding: 0 20rpx;
		background-color: white;
	}
	.search-history{
		.title{
			display: flex;
			justify-content: space-between;
			.icon-box{
				color: #DD524D;
			}
		}
	}
	.history-box{
		padding-top: 20rpx;
		height: 30vh;
		border-bottom: 2rpx solid #C8C7CC;
		overflow: hidden;
		.forAWhite{
			color: #999999;
			text-align: center;
		}
		.hasHistory{
			display: flex;
			flex-wrap: wrap;
			// width: 80%;
			.history-item{
				background-color: rgba(0,0,0,.1);
				letter-spacing: 1rpx;
				margin: 10rpx;
				padding: 10rpx;
				border-radius: 10rpx;
			}
		}
	}
	
</style>
