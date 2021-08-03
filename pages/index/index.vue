<template>
	<view class="index">
		<view @click="search">
			<search></search>
		</view>
		<!-- 轮播图 -->
		<view class="box">
			<view class="index-swiper">
				<swiper 
				indicator-dots="true" 
				autoplay="true"
				circular="true"
				>
					<swiper-item v-for="item in swipers"><image :src="item.src"></image></swiper-item>
				</swiper>
			</view>
			<classify :name="name"></classify>
			<fourth :fourthData="fourthData"></fourth>
			<book-rec :bookInfo="bookInfo"></book-rec>
			<new-book :newBookShow="newBookShow"></new-book>
		</view>
	</view>
</template>

<script>
	import search from '../../component/search.vue'
	import classify from '../../component/classify.vue'
	import fourth from '../../component/fourths.vue'
	import bookRec from '../../component/bookRecommend.vue'
	import newBook from '../../component/newBook.vue'
	export default {
		data() {
			return {
				swipers: [
					{
						"src":"https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg"
					},
					{
						"src": "https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg"
					}
				],
				name:[
					{
						'img':'iconfont icon-jiaohuan',
						'name':'交换图书'
					},
					{
						'img':'iconfont icon-yiwu',
						'name':'以书易物'
					},
					{
						'img':'iconfont icon-chushou',
						'name':'出售图书'
					},
					{
						'img':'iconfont icon-jiaoliu',
						'name':'书评交流'
					}
				],
				fourthData: [
					{
						'title': '新增书籍',
						'subhead': '发现好书',
						'url': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg'
					},
					{
						'title': '新增书籍',
						'subhead': '发现好书',
						'url': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg'
					},
					{
						'title': '新增书籍',
						'subhead': '发现好书',
						'url': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg'
					},
					{
						'title': '新增书籍',
						'subhead': '发现好书',
						'url': 'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg'
					}
				],
				bookInfo: [
					{
						'img':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'title': '唐诗全集',
						'writer': '陈卓越',
						'style': '以书易书'
					},
					{
						'img':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'title': '唐诗全集',
						'writer': '陈卓越',
						'style': '以书易书'
					},
					{
						'img':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'title': '唐诗全集',
						'writer': '陈卓越',
						'style': '以书易书'
					},
					{
						'img':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'title': '唐诗全集',
						'writer': '陈卓越',
						'style': '以书易书'
					}
				],
				newBookShow: [
					{
						'src':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'infoTitle': '陈卓越著作唐诗全集，非常简单易懂,非常好用',
						'infoContent': '这是一部非常厉害的书籍，记录了陈卓越最喜欢的故事。'
					},
					{
						'src':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'infoTitle': '陈卓越著作唐诗全集，非常简单易懂,非常好用',
						'infoContent': '这是一部非常厉害的书籍，记录了陈卓越最喜欢的故事。'
					},
					{
						'src':'https://www.z4a.net/images/2021/07/31/62076476_p4_master1200.jpg',
						'infoTitle': '陈卓越著作唐诗全集，非常简单易懂,非常好用',
						'infoContent': '这是一部非常厉害的书籍，记录了陈卓越最喜欢的故事。'
					}
				]
				
			}
		},
		methods: {
			search(){
				uni.navigateTo({
					url:"../search/search"
				})
			}
		},
		components:{
			search,
			classify,
			fourth,
			bookRec,
			newBook
		}
	}
</script>

<style lang="less">
	.search{
		padding: 0 20rpx;
	}
	.index-swiper{
		margin-bottom: 10rpx;
		swiper{
			width: 710rpx;
			height: 300rpx;
			margin: 0 20rpx 40rpx 20rpx;
			swiper-item{
				image{
					text-align: center;
					width: 100%;
					height: 100%;
					border-radius: 10rpx;
				}
			}
		}
	}
	.fourth,.book-rec{
		border-bottom: 20rpx solid rgba(0,0,0,.1);
	}
	
</style>
