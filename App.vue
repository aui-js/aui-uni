<script>
	export default {
		onLaunch: function() {
			console.log('App Launch');
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
	/*每个页面公共css */
	@import url("./common/aui/css/aui.css");
	@import url("./common/aui/css/aui.iconfont.css");
	uni-page-head{
		display: none;
	}
	uni-page-wrapper{
		height: 100vh !important;
	}
	uni-tabbar .uni-tabbar-border{background: rgba(100,100,100,.3) !important; transform: scaleY(.3) !important;}
	uni-tabbar .uni-tabbar__icon{
		width: 30px; 
		height: 30px; 
		/* #ifdef MP */
		width: 25px;
		height: 25px; 
		/* #endif */
		margin-top: 5px;
	}	
	uni-tabbar .uni-tabbar__icon img{
		width: 30px;
		height: 30px; 
		/* #ifdef MP */
		width: 25px;
		height: 25px; 
		/* #endif */
	}
	uni-tabbar .uni-tabbar__label{
		top: -5px;
	}
</style>
