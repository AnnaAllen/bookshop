<template>
	<view class="find">
		<view class="fixed-box">
			<view @click="search">
				<search></search>
			</view>
			<navi :naviItem="naviItem"></navi>
		</view>
		<view class="top">
			<shop-item :userInfo="userInfo" @changeUserLike='changeUserLike'></shop-item>
		</view>
	</view>
</template>

<script>
	import navi from "../../component/navigation.vue"
	import search from '../../component/search.vue'
	import shopItem from "../../component/shopItem.vue"
	export default {
		data() {
			return {
				userSearchData: '',
				naviItem: ['推荐','易书','易物','出售','书评'],
				userInfo: [
					{
						'userID': 1,
						'userP': '//img3m3.ddimg.cn/3/5/28542693-1_w_11.jpg',
						'userContent': '消失的13级台阶（罗翔推荐！荣获日本推理小说至高荣誉江户川乱步奖！是否值得为一场痛快的复仇，陪葬掉自己的人生？）',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen1111111111111111111',
						'userLike': 90,
						'style': 0,
						'isLike': true
					},
					{
						'userID': 2,
						'userP': '//img3m2.ddimg.cn/1/6/29239552-1_w_18.jpg',
						'userContent': '字母表谜案（怪异君推荐！当你隐隐觉得不对劲，致命的恶意正悄悄逼近！大山诚一郎封神之作！）（读客悬疑文库）',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen',
						'userLike': 90,
						'style': 1,
						'isLike': false
					},
					{
						'userID': 3,
						'userP': '//img3m1.ddimg.cn/17/6/25223831-1_w_3.jpg',
						'userContent': ' 必须找到阿历克斯（横扫25国的重磅推理小说！荣获国际匕首奖）',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen',
						'userLike': 90,
						'style': 2,
						'isLike': true
					},
					{
						'userID': 4,
						'userP': '//img3m2.ddimg.cn/57/35/28978842-1_w_3.jpg',
						'userContent': '短篇推理之神三大神作（教你看穿杀人诡计！诡计博物馆+绝对不在场证明+密室收藏家。拿遍推理大奖！绫辻行人、麻耶雄嵩推荐）',
						'userImg': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'userName': 'AnnaAllen',
						'userLike': 90,
						'style': 2,
						'isLike': false
					},
					{
						'userID': 4,
						'userP': '//img3m2.ddimg.cn/57/35/28978842-1_w_3.jpg',
						'userContent': '短篇推理之神三大神作（教你看穿杀人诡计！诡计博物馆+绝对不在场证明+密室收藏家。拿遍推理大奖！绫辻行人、麻耶雄嵩推荐）',
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
			navi,
			search,
			shopItem
		},
		methods:{
			search(){
				uni.navigateTo({
					url:"../search/search"
				})
			},
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
		}
	}
</script>

<style lang="less" scoped>
	.fixed-box{
		padding: 0 20rpx 30rpx 20rpx;
		z-index: 9;
		background-color: white;
	}
	.top{
		padding: 0 20rpx;
	}
	
</style>
