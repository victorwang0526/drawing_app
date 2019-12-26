<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	*{
		margin: 0;
		padding: 0;
	}
	/*每个页面公共css */
	.g-flex-main{
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		overflow: hidden;
		line-height: 1.5;
		font-size: 20rpx;
	}
    .m-flex-main{
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        overflow: hidden;
    }
	.g-flex-box,.m-flex-box{
		flex: 1;
		overflow-y: auto;
	}
	.g-flex-column{
		width: 100%;
		height: 100%;
		display: flex;
		flex-flow: row nowrap;
	}
	.flex-col-3{
		width: 33.33%;
		flex: 1;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.flex-col-2{
		width: 50%;
		flex: 1;
	}
    .common-nav{
        display: flex;
        align-items: center;
        justify-content: center;
        height: 40rpx;
        line-height: 40rpx;
        font-size: 14rpx;
    }
    .nav-col{
        position: relative;
        flex: 1;
        color: #333;
        text-align: center;
        height: 40rpx;
        line-height: 40rpx;
    }
    .nav-col.active:before{
        position: absolute;
        left: 50%;
        bottom: 0;
        content: "";
        height: 1rpx;
        width: 40rpx;
        margin-left: -20rpx;
        background: #3880ff;
    }
    .nav-col.active{
        color: #3880ff;
    }
    .bg-red {
        background-color: #f8654e;
    }
    .bg-orange {
        background-color: #f2ab4f;
    }
    .bg-green {
        background-color: #8fb131;
    }
    .bg-disabled {
        background-color: #363b3d;
    }
</style>
