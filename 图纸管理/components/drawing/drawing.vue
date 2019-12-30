<template>
	<div v-show="show" style="width: 100%; height: 100%; position: relative;">
		<div class="fixation-handle">
			<button @click="zoomChange(1)">
				+
			</button>
			<button @click="zoomChange(-1)">
				-
			</button>
			<button @click="rotateChange(1)">
				←
			</button>
			<button @click="rotateChange(-1)">
				→
			</button>
		</div>
		<div :style="{height: h + 'px', width: w + 'px', overflow: 'auto'}">
			<canvas :canvas-id="cid" :id="cid" :ref="cid" :style="{height: ch + 'px', width: cw + 'px'}"></canvas>
		</div>
		<div v-if="showLoading" class="wrapper-loading" @click.stop>
			<img src="../../static/loading.svg" alt="">
		</div>
	</div>

</template>

<script>
	export default {
		name: 'drawing',
		props: {
			imgUrl: String,
			cid: String,
			w: Number,
			h: Number
		},
		data() {
			return {
				scaleSize: 1,
				zoomStep: 0.2,
				rotate: 0,
				rotateStep: 90,
				showLoading: true,
				canvas: null,
				context: null,
				img: {
					height: 0,
					width: 0
				},
				cw: 0, // canvas width
				ch: 0, // canvas height
				show: true
			}
		},
		watch: {
			show: function(val) {
				console.log(val)
				if(val) {
					console.log('drawing show...')
					this.drawImg()
				}
			}
		},
		mounted() {
			this.context = uni.createCanvasContext(this.cid, this)
			const _this = this
			uni.getImageInfo({
				src: 'http://47.110.45.52:8085' + this.imgUrl,
				success: function (image) {
					_this.showLoading = false
					_this.img = image
					_this.drawImg()
				}
			});
		},
		methods: {
			drawImg() {
				this.context.save()
				let tx = 0
				let ty = 0
				let width = 0
				let height = 0
				if(this.rotate === 0 || this.rotate === 180) {
					width = this.img.width * this.scaleSize
					height = this.img.height * this.scaleSize
					if(this.rotate === 180) {
						ty = this.img.height * this.scaleSize
						tx = this.img.width * this.scaleSize
					}
				}else {
					width = this.img.height * this.scaleSize
					height = this.img.width * this.scaleSize
					if(this.rotate === 90) {
						tx = this.img.height * this.scaleSize
					}else if(this.rotate === 270) {
						ty = this.img.width * this.scaleSize
					}
				}
				this.cw = width
				this.ch = height
				this.context.translate(tx, ty)
				this.context.scale(this.scaleSize, this.scaleSize);
				this.context.rotate(this.rotate * Math.PI / 180)
				let _this = this
				setTimeout(() => {
					_this.context.drawImage(_this.img.path, 0, 0);
					_this.context.draw()
				}, 100)
			},
			zoomChange(seed) {
				this.scaleSize = this.scaleSize * (1 + seed * this.zoomStep)
				this.drawImg()
			},
			rotateChange(seed) {
				this.rotate = this.rotate + this.rotateStep * seed;
				if(this.rotate < 0 || this.rotate >= 360) {
					this.rotate = 0
				}
				this.drawImg()
			}
		}
	}
</script>

<style scoped>
	.wrapper-loading {
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		z-index: 9;
		display: flex;
		align-items: center;
		justify-content: center;
		height: 100%;
	}
	.img-div {
		width: 100%;
		height: 100%;
		background-color: #2c3e50;
		/*margin:.1rem;*/
		/*padding: 1rem;*/
		display: flex;
		align-items: center;
		justify-content: center;
		overflow: auto;
		/*box-sizing: border-box;*/
	}
	.img-div img{
		max-width: inherit;
		display: block;
	}
	.fixation-handle{
		position: absolute;
		right: 2rem;
		bottom: 10%;
		z-index: 1;
		background: rgba(0,0,0,.6);
	}
</style>
