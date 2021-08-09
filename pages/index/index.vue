<template>
	<view class="index">
		<view @click="search">
			<search></search>
		</view>
		<view class="box">
			<!-- 轮播图 -->
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
						"src":"http://img61.ddimg.cn/upload_img/00316/by/750x315-1625025326.jpg"
					},
					{
						"src": "http://img62.ddimg.cn/upload_img/00881/1111/750X315_20210806-1628235092.jpg"
					}
				],
				name:[
					{
						'img':'iconfont icon-jiaohuan',
						'name':'交换图书',
						'url': '../find/find'
					},
					{
						'img':'iconfont icon-yiwu',
						'name':'以书易物',
						'url': '../find/find'
					},
					{
						'img':'iconfont icon-chushou',
						'name':'出售图书',
						'url': '../find/find'
					},
					{
						'img':'iconfont icon-jiaoliu',
						'name':'书评交流',
						'url': '../find/find'
					}
				],
				fourthData: [
					{
						'title': '新增书籍',
						'subhead': '发现好书',
						'src': '../fourthDetail/fourthDetail',
						'fouthStyle': 1,
						'url': 'http://img3m4.ddimg.cn/49/23/29256034-1_l_30.jpg'
					},
					{
						'title': '推荐书籍',
						'subhead': '发现好书',
						'src': '../fourthDetail/fourthDetail',
						'fouthStyle': 2,
						'url': '//img3m6.ddimg.cn/70/7/29171806-1_w_6.jpg'
					},
					{
						'title': '热门浏览',
						'subhead': '发现好书',
						'src': '../fourthDetail/fourthDetail',
						'fouthStyle': 3,
						'url': '//img3m5.ddimg.cn/24/24/28963365-1_w_6.jpg'
					},
					{
						'title': '大热书评',
						'subhead': '发现好书',
						'src': '../fourthDetail/fourthDetail',
						'fouthStyle': 4,
						'url': '//img3m4.ddimg.cn/93/13/28536744-1_w_3.jpg'
					}
				],
				bookInfo: [
					{
						'img':'//img3m0.ddimg.cn/64/34/29192590-1_w_11.jpg',
						'title': '唐诗全集',
						'writer': '陈卓越',
						'style': '以书易书'
					},
					{
						'img':'//img3m5.ddimg.cn/44/30/23999525-5_u_23.jpg',
						'title': '唐诗全集',
						'writer': '陈卓越',
						'style': '以书易书'
					},
					{
						'img':'//img3m8.ddimg.cn/25/27/29278978-1_w_1440.jpg',
						'title': '唐诗全集',
						'writer': '陈卓越',
						'style': '以书易书'
					},
					{
						'img':'//img3m9.ddimg.cn/97/25/28996999-4_u_27.jpg',
						'title': '唐诗全集',
						'writer': '陈卓越',
						'style': '以书易书'
					}
				],
				newBookShow: [
					{
						'src':'//img3m5.ddimg.cn/44/30/23999525-5_u_23.jpg',
						'infoTitle': '陈卓越著作唐诗全集，非常简单易懂,非常好用',
						'infoContent': '这是一部非常厉害的书籍，记录了陈卓越最喜欢的故事。'
					},
					{
						'src':'//img3m7.ddimg.cn/97/21/23618527-1_w_3.jpg',
						'infoTitle': '陈卓越著作唐诗全集，非常简单易懂,非常好用',
						'infoContent': '这是一部非常厉害的书籍，记录了陈卓越最喜欢的故事。'
					},
					{
						'src':'//img3m7.ddimg.cn/97/21/23618527-1_w_3.jpg',
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
