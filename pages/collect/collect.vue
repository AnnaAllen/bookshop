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
						'title': '一不小心把东西全都删掉了，救命啊',
						'content': '又要从头开始写逻辑和数据，救命啊啊啊啊啊',
						'image': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg'
					},
					{
						'writerImg':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'writer': 'Anna',
						'writerId': 1,
						'attention':true,
						'title': '一不小心把东西全都删掉了，救命啊',
						'content': '又要从头开始写逻辑和数据，救命啊啊啊啊啊',
						'image': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg'
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
