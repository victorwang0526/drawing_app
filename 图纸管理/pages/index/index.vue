<template>
	<view class="g-flex-main">
		<view class="g-flex-column">
			<view class="flex-col-3 bg-red">
				<view class="flex-middle">
					<image class="home-img" src="../../static/1.png" mode="aspectFit"></image>
					<view class="home-title">小胖墩1号</view>
					<text class="home-sub-title">一个小胖墩</text>
				</view>
			</view>
			<view class="flex-col-3 bg-orange">
				<view class="flex-middle">
					<image class="home-img" src="../../static/1.png" mode="aspectFit"></image>
					<view class="home-title">小胖墩1号</view>
					<text class="home-sub-title">一个小胖墩</text>
				</view>
			</view>
			<view class="flex-col-3 bg-green">
				<view class="flex-middle">
					<image class="home-img" src="../../static/1.png" mode="aspectFit"></image>
					<view class="home-title">小胖墩1号</view>
					<text class="home-sub-title">一个小胖墩</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

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
