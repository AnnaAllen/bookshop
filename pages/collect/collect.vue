<template>
	<view>
		<view class="item-box1">
			<view class="like-num">{{userCllect.length}}个物品</view>
			<view :class="iconDot"></view>
		</view>
		<user-like-item :userCllect='userCllect' @getNewAtten="getNewAtten"></user-like-item>
	</view>
</template>

<script>
	import userLikeItem from '../../component/userLikeItem.vue'
	export default {
		data() {
			return {
				iconDot: 'iconfont icon-bk-dot',
				userCllect: [
					{
						'writerImg':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'writer': 'Anna',
						'writerId': 1,
						'attention':true,
						'title': '短篇推理之神三大神作（教你看穿杀人诡计！诡计博物馆+绝对不在场证明+密室收藏家。拿遍推理大奖！绫辻行人、麻耶雄嵩推荐）',
						'bookStyle': '以书易物',
						'price': null,
						'bookStyleNum': 0,
						'content': '拿遍推理大奖，横扫推理榜单！大山诚一郎烧脑推理合集：尘封悬案、完美不在场证明、密室诡计。快节奏、零废话、神反转，教你一眼看穿诡计三大类型！读客熊猫君出品',
						'image': 'https://img3m2.ddimg.cn/57/35/28978842-1_w_3.jpg'
					},
					{
						'writerImg':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'writer': 'Allen',
						'writerId': 2,
						'attention':false,
						'title': '希望之线（东野圭吾新代表作，高分作品TOP5！）',
						'bookStyle': '出售图书',
						'bookStyleNum': 2,
						'price': 40,
						'content': '《白夜行》《嫌疑人X的献身》《解忧杂货店》《恶意》后，豆瓣东野圭吾第五高分新作！好看到爆炸的人情推理长篇。上市首周登顶日本畅销书总榜，周刊文春推理榜年度推荐。 ',
						'image': '//img3m3.ddimg.cn/39/28/29216523-1_w_27.jpg'
					}
				]
			}
		},
		methods: {
			getNewAtten(id){
				this.userCllect.forEach(item => {
					if(id == item.writerId){
						item.attention = !item.attention
					}
				})
			}
		},
		components:{
			userLikeItem
		}
	}
</script>

<style lang="less" scoped>
	.item-box1{
		display: flex;
		justify-content: space-between;
		background-color: #F1F1F1;
		color: #999999;
		padding: 10rpx 20rpx;
		text-align: center;
	}
</style>
