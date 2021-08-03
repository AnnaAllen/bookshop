<template>
	<view class="navi">
		<view class="navi-item">
			<view 
			class="recommend" 
			v-for="(item,index) in naviItem"
			@click="select(index)"
			>
				<view :class="{active: index == current}">
					<text>{{item}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				current: 0
			}
		},
		props:[
			'naviItem'
		],
		methods:{
			select(index){
				//选择到该view时，显示下面的border
				this.current = index
			}
		}
	}
</script>

<style lang="less" scoped>
	.navi{
		.navi-item{
			display: flex;
			
			.recommend{
				text-align: center;
				flex: 1;
			}
			.active{
				text{
					border-bottom: 6rpx solid #DD524D;
					padding: 10rpx;
				}
			}
		}
	}
</style>
