<template>
	<view class="my">
		<view class="padd">
			<user-info :userInfo="userInfo" class="user-info"></user-info>
		</view>
		<user-info2 :num="num" :goods='goods'></user-info2>
		<view class="border-type"></view>
	</view>
</template>

<script>
	import userInfo from '../../component/userInfo.vue'
	import userInfo2 from '../../component/userInfo2.vue'
	import classify from '../../component/classify.vue'
	export default {
		data() {
			return {
				userInfo: {
					userImg:'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
					userName: 'Anna',
					userId: 111
				},
				num:[0,1,2,4],
				goods:['我发布的','我转手的','我的喜欢','我的书评']
			}
		},
		methods: {
			
		},
		components:{
			userInfo,
			userInfo2,
			
		}
	}
</script>

<style scoped lang="less">
	.my{
		padding: 20rpx;
	}
	.padd{
		padding: 20rpx 0;
	}
	.border-type{
		padding-top: 20rpx;
		border-bottom: 2rpx solid #C8C7CC;
	}
</style>
