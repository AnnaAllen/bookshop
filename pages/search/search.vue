<template>
	<view class="big-box">
		<view class="searchPage">
			<search></search>
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
					<view class="history-item" v-for="(item,index) in historyData" @click="userInput(index)">
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
				clickHistoryData: '',
				historyData: ['水','火','夜神月','misa','L','death','Note','推理小说']
			}
		},
		methods: {
			deleteData(){
				this.historyData = null
			},
			//点击数组中原有的数据后，1.加入历史数组 2.将点击的数据放入缓存 3.跳转到找书页面
			userInput(num){
				this.clickHistoryData = this.historyData[num]
				uni.setStorageSync('searchData',this.clickHistoryData)
				this.historyData.push(uni.getStorageSync('searchData'))
				uni.navigateTo({
					url:'../findBook/findBook'
				})
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
		height: 34vh;
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
