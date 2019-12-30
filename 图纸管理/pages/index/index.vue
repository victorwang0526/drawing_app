<template>
	<view class="g-flex-main" ref="home" id="home">
		<view class="g-flex-column">
			<view class="flex-col-3" v-for="i in [0, 1, 2]" :key="i"
				  v-bind:class="{'bg-disable': tasks.length <= i, 'bg-red': i === 0 && tasks.length > i, 'bg-orange': i === 1 && tasks.length > i, 'bg-green': i === 2 && tasks.length > i}"
				  @click="openDetail(i)">
				<view class="flex-middle">
					<image v-if="i === 0 && i < tasks.length" src="../../static/img1.svg" class="home-img" mode="aspectFit"></image>
					<image v-if="i === 1 && i < tasks.length" src="../../static/img2.svg" class="task-img" mode="aspectFit"></image>
					<image v-if="i === 2 && i < tasks.length" src="../../static/img3.svg" class="task-img" mode="aspectFit"></image>
					<image v-if="tasks.length <= i" src="../../static/disable.svg" class="task-img"></image>
<!--					<image class="home-img" :src="i >= tasks.length ? '' : 'http://47.110.45.52:8085' + tasks[i].map1" mode="aspectFit"></image>-->
					<view class="home-title">{{i >= tasks.length ? '暂无任务' : tasks[i].name}}</view>
					<text class="home-sub-title">{{i >= tasks.length ? '-' : tasks[i].description}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				tasks: [],
				colClasses: ['bg-red', 'bg-orange', 'bg-green']
			}
		},
		onLoad() {
			uni.request({
				url: 'http://47.110.45.52:8085/api/task/task',
				success: (res) => {
					this.tasks = res.data.list
				}
			})
		},
		computed: {
			colClass() {
				return function(i) {
					let imgC = 'bg-disabled'
					if(this.tasks.length > i) {
						imgC = this.colClasses[i]
					}
					return {
						[imgC]: true
					}
				}
			}
		},
		methods: {
			openDetail(i) {
				if(i >= this.tasks.length) {
					return
				}
				uni.createSelectorQuery().select('#home').fields({
					size: true,
					scrollOffset: true
				}, (data) => {
					uni.navigateTo({
						url: '/pages/task-detail/task-detail?w='+data.width+'&h='+data.height+'&task=' + encodeURIComponent(JSON.stringify(this.tasks[i]))
					})
				}).exec();
			}
		}
	}
</script>

<style scoped>
	.flex-middle{
		color: #fff;
		text-align: center;
	}
	.home-img{
		width: 100rpx;
		height: 100rpx;
		display: block;
		margin: 0 auto 28rpx;
		display: block;
	}
	.home-img div{
		background-size: cover;
	}
	.home-title{
		font-size: 26rpx;
	}
	.home-sub-title{
		font-size: 16rpx;
	}
</style>
