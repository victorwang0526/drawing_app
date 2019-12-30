<template>
	<view class="g-flex-main">
		<view class="g-flex-column">
			<view class="flex-col-2 m-flex-main">
				<view class="common-nav">
					<view class="nav-col active">图纸</view>
				</view>
				<drawing :cid="'tz1'" :imgUrl="task.map1" :w="w" :h="h"></drawing>
			</view>
			<view class="flex-col-2 m-flex-main">
				<view class="common-nav">
					<view class="nav-col" v-bind:class="{active: tab2Actived === 't21'}"
						  v-if="task.map2 !== ''" @click="openTab('t21')">工艺图纸</view>
					<view class="nav-col" v-bind:class="{active: tab2Actived === 't22'}"
						  v-if="task.map3 !== ''" @click="openTab('t22')">操作图纸</view>
					<view class="nav-col" v-bind:class="{active: tab2Actived === 't23'}"
						  v-if="task.map4 !== ''" @click="openTab('t23')">操作图纸2</view>
				</view>
				<drawing v-if="task.map2 !== ''" v-show="tab2Actived === 't21'" ref="t21"
						 :cid="'tz21'" :imgUrl="task.map2" :w="w" :h="h"></drawing>
				<drawing v-if="task.map3 !== ''" v-show="tab2Actived === 't22'" ref="t22"
						 :cid="'tz22'" :imgUrl="task.map3" :w="w" :h="h"></drawing>
				<drawing v-if="task.map4 !== ''" v-show="tab2Actived === 't23'" ref="t23"
						 :cid="'tz23'" :imgUrl="task.map4" :w="w" :h="h"></drawing>
			</view>
		</view>
	</view>
</template>

<script>
	import drawing from "../../components/drawing/drawing";
	export default {
		components: {
			drawing
		},
		data() {
			return {
				tab2Actived: '',
				task: null,
				w: 0,
				h: 0
			};
		},
		onLoad: function(option) {
			this.task = JSON.parse(decodeURIComponent(option.task))
			this.w = Number.parseInt(option.w) / 2 - 15
			this.h = Number.parseInt(option.h) - 65
			this.tab2Actived = 't21'
		},
		methods: {
			openTab(tabId) {
				this.tab2Actived = tabId
				if(tabId === 't21') {
					this.$refs.t21.drawImg()
				}else if(tabId === 't22') {
					this.$refs.t22.drawImg()
				}else if(tabId === 't23') {
					this.$refs.t23.drawImg()
				}
			}
		},
	}
</script>

<style scoped>

</style>
