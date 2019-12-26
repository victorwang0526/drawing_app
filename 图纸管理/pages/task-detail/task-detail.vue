<template>
	<view class="g-flex-main">
			<view class="g-flex-column">
				<view class="flex-col-2 m-flex-main">
					<view class="common-nav">
						<view class="nav-col active">图纸</view>
					</view>
					<view class="m-flex-box">
						<view class="scroll-pic">
							<image src="../../static/1.png" :style="{transform: `rotate(${this.rotate}deg) scale(${this.zoom})`}" mode="aspectFit">
							</image>
						</view>
					</view>
				</view>
				<view class="flex-col-2 m-flex-main">
					<view class="common-nav">
						<view class="nav-col active">工艺图纸</view>
						<view class="nav-col">图纸</view>
						<view class="nav-col">工艺图纸</view>
						<view class="nav-col">图纸</view>
					</view>
					<view class="m-flex-box">
						<view class="scroll-pic">
							<image src="../../static/1.png" :style="{transform: `rotate(${this.rotate}deg) scale(${this.zoom})`}" mode="aspectFit">
							</image>
						</view>
					</view>
				</view>
			</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style scoped>
	.m-flex-box{
		padding: 8rpx;
		background-color: #363b3d;
		margin: 0 1px;
	}
	.m-flex-box:first-child{
		margin-left: 0;
	}
	.m-flex-box:last-child{
		margin-right: 0;
	}
	.scroll-pic{
		width: 100%;
		height: 100%;
		overflow: auto;
		
	}
	.scroll-pic image{
		width: 100%;
		height: 100%;
		display: block;
	}
</style>
