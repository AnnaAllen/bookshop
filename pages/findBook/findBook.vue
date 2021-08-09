<template>
	<view class="find-book">
		<view class="user-search-info">
			根据您搜索“{{searchInfo}}”推荐
		</view>
		<view class="book-item">
			<shop-item :userInfo="userInfo"></shop-item>
		</view>
	</view>
</template>

<script>
	import shopItem from '../../component/shopItem.vue'
	export default {
		data() {
			return {
				searchInfo: '',
				userInfo: [
					{
						'userID': 1,
						'userP': '//img3m7.ddimg.cn/77/26/28992227-1_w_18.jpg',
						'userContent': '有没有姐妹喜欢啊，这本书很好看的！给姐妹们安利',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen1111111111111111111',
						'userLike': 90,
						'style': 0,
						'isLike': true
					},
					{
						'userID': 2,
						'userP': '//img3m7.ddimg.cn/77/26/28992227-1_w_18.jpg',
						'userContent': '有没有姐妹喜欢啊，这本书很好看的！给姐妹们安利',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen',
						'userLike': 90,
						'style': 1,
						'isLike': false
					},
					{
						'userID': 3,
						'userP': '//img3m7.ddimg.cn/77/26/28992227-1_w_18.jpg',
						'userContent': '有没有姐妹喜欢啊，这本书很好看的！给姐妹们安利.',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen',
						'userLike': 90,
						'style': 2,
						'isLike': true
					},
					{
						'userID': 4,
						'userP': '//img3m7.ddimg.cn/77/26/28992227-1_w_18.jpg',
						'userContent': '有没有姐妹喜欢啊，这本书很好看的！给姐妹们安利.',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen',
						'userLike': 90,
						'style': 2,
						'isLike': false
					}
				],
			}
		},
		components:{
			shopItem
		},
		methods: {
			
		},
		onShow() {
			this.searchInfo = uni.getStorageSync('searchData')
		}
	}
</script>

<style scoped lang="less">
	.find-book{
		padding: 20rpx;
		.user-search-info{
			padding-bottom: 20rpx;
		}
	}
</style>
