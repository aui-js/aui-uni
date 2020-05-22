<template name="aui-footer">
	<view class="aui-footer row-before">
		<view class="aui-footer-list active" onclick="aui.openWin('index.html')">
			<view class="iconfont iconjs"></view><view class="aui-footer-text">API</view>
		</view>
		<view class="aui-footer-list" onclick="aui.openWin('demo/demo-index.html')">
			<view class="iconfont iconshilidaima"></view><view class="aui-footer-text">DEMO</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'aui-footer',
		data() {
			return {
				
			};
		}
	}
</script>

<style>
	.aui-footer{
		width: 100vw;
		height: 55px;
		background: #FFF;
		display: flex;
		justify-content: space-around;
		white-space: nowrap;
		position: fixed !important;
		bottom: 0;
		left: 0;
		z-index: 997;
	}
	.aui-footer-list{
		padding: 7px 20px 3px 20px;
		max-width: 25%;
		text-align: center;
		flex: 1;
		box-sizing: border-box;
		display: inline-block;
	}
	.aui-footer-list .iconfont{
		width: 100%;
		height: 25px;
		line-height: 28px;
		display: inline-block;
		font-size: 22px;	
		background: linear-gradient(to right, #AAA, #CDCDCD);
		-webkit-background-clip: text;
		color: transparent;
	}
	.aui-footer-list .aui-footer-text{
		width: 100%;
		height: 20px;
		line-height: 20px;
		font-size: 12px;
		background: linear-gradient(to right, #AAA, #CDCDCD);
		-webkit-background-clip: text;
		color: transparent;
	}
	.aui-footer-list.active .iconfont,.aui-footer-list.active .aui-footer-text{
		background: linear-gradient(to right, #197DE0, #73B9EC);
		-webkit-background-clip: text;
		color: transparent;
	}
</style>
