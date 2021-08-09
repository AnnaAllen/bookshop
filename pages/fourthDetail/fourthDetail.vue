<template>
	<view class="fourth-detail">
		<user-like-item :userCllect="userCllect"></user-like-item>
	</view>
</template>

<script>
	import userLikeItem from '../../component/userLikeItem.vue'
	export default {
		data() {
			return {
				userCllect: [
					{
						'writerImg':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'writer': 'Anna',
						'writerId': 1,
						'attention':true,
						'title': '一不小心把东西全都删掉了，救命',
						'bookStyle': '以书易物',
						'price': null,
						'bookStyleNum': 0,
						'content': '又要从头开始写逻辑和数据',
						'image': '//img3m7.ddimg.cn/77/26/28992227-1_w_18.jpg'
					},
					{
						'writerImg':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'writer': 'Allen',
						'writerId': 2,
						'attention':false,
						'title': '9命，为什么两个重复了',
						'bookStyle': '出售图书',
						'bookStyleNum': 2,
						'price': 40,
						'content': '又要从头开始写逻辑和数据',
						'image': '//img3m7.ddimg.cn/77/26/28992227-1_w_18.jpg'
					},
					{
						'writerImg':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'writer': 'Allen',
						'writerId': 2,
						'attention':false,
						'title': '这本书太好看了，我给大家推荐它！',
						'bookStyle': '交流书评',
						'bookStyleNum': 3,
						'price': null,
						'content': '',
						'image': '//img3m7.ddimg.cn/77/26/28992227-1_w_18.jpg'
					}
				]
			}
		},
		methods: {
			
		},
		components:{
			userLikeItem
		}
	}
</script>

<style scoped lang="less">
	.fourth-detail{
		
	}
</style>
