<template>
	<view class="find">
		<view class="fixed-box">
			<search></search>
			<navi :naviItem="naviItem"></navi>
		</view>
		<view class="top">
			<shop-item :userInfo="userInfo" @changeUserLike='changeUserLike'></shop-item>
		</view>
		<button type="default"  @click='getSearchData'>getDAta</button>
	</view>
</template>

<script>
	import navi from "../../component/navigation.vue"
	import search from '../../component/search.vue'
	import shopItem from "../../component/shopItem.vue"
	export default {
		data() {
			return {
				naviItem: ['推荐','易书','易物','出售','书评'],
				userInfo: [
					{
						'userID': 1,
						'userP': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userContent': '有没有姐妹喜欢啊，这本书很好看的！给姐妹们安利，我CP就是最真的',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen1111111111111111111',
						'userLike': 90,
						'style': 0,
						'isLike': true
					},
					{
						'userID': 2,
						'userP': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userContent': '有没有姐妹喜欢啊，这本书很好看的！给姐妹们安利，我CP就是最真的',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen',
						'userLike': 90,
						'style': 1,
						'isLike': false
					},
					{
						'userID': 3,
						'userP': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userContent': '有没有姐妹喜欢啊，这本书很好看的！给姐妹们安利，我CP就是最真的',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen',
						'userLike': 90,
						'style': 2,
						'isLike': true
					},
					{
						'userID': 4,
						'userP': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userContent': '有没有姐妹喜欢啊，这本书很好看的！给姐妹们安利，我CP就是最真的',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen',
						'userLike': 90,
						'style': 2,
						'isLike': false
					}
				],
				searchData: '111'
			}
		},
		components:{
			navi,
			search,
			shopItem
		},
		methods:{
			changeUserLike(userID){
				this.userInfo.forEach(function(item){
					if(item.userID == userID){
						item.isLike = !item.isLike
						if(item.isLike){
							item.userLike++
						}else {
							item.userLike--
						}
					}
					
				})
			},
			getSearchData(){
				this.searchData = uni.getStorageSync('searchData')
				console.log(this.searchData)
			}
		},
		onShow(){
			//获取缓存中的参数
			this.getSearchData()
		},
	}
</script>

<style lang="less" scoped>
	.fixed-box{
		padding: 0 20rpx;
		z-index: 9;
		background-color: white;
	}
	
</style>
