<template>
	<view class="aui-loading aui-loading-ring" v-if="show && type == 1">
		<view class="aui-mask" v-if="mask"></view>
		<view class="aui-loading-main">
			<view class="aui-loading-animate">
				<view class="span"></view>
				<view class="span"></view>
				<view class="span"></view>
				<view class="span"></view>
				<view class="span"></view>
				<view class="span"></view>
				<view class="span"></view>
				<view class="span"></view>
				<view class="span"></view>
				<view class="span"></view>
				<view class="span"></view>
				<view class="span"></view>
			</view>
			<view class="aui-loading-msg">{{msg}}<view class="dotting"></view></view>
		</view>
	</view>
	<view class="aui-loading aui-loading-dots" v-else-if="show && type == 4">
		<view class="aui-mask" v-if="mask"></view>
		<view class="aui-loading-main">
			<view class="aui-loading-dot-items">
				<view class="aui-loading-dot-item" id="dot_one"></view>
				<view class="aui-loading-dot-item" id="dot_two"></view>
				<view class="aui-loading-dot-item" id="dot_three"></view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "aui-loading",
		props: {
			show: {
				type: Boolean,
				default: false
			},
			type: {
				type: Number,
				default: 1
			},
			msg: {
				type: String,
				default: ''
			},
			mask: {
				type: Boolean,
				default: true
			},
			direction: {
				type: String,
				default: 'col'
			},
			theme: {
				type: Number,
				default: 1
			}
		},
		data() {
			return {
				show: this.show,
				type: this.type,
				msg: this.msg,
				mask: this.mask,
				direction: this.direction,
				theme: this.theme
			};
		},
		created(){
			console.log(this.type);
		},
	}
</script>

<style>
	/* 遮罩层样式 */
	.aui-mask{
		width: 100%;
		height: 100%;
		background: rgba(0,0,0,.4);
		-ms-animation: aui-fade-in .2s ease-out forwards;
		-webkit-animation: aui-fade-in .2s ease-out forwards;
		animation: aui-fade-in .2s ease-out forwards;
		position: fixed;
		top: 0px;
		left: 0px;
		z-index: 998;
	}
	
	/* loading加载弹窗 */
	/* loading-ring 样式设置 */
	.aui-loading.aui-loading-ring{
		width: 100%;
		height: 100%;
		position: fixed;
		top: 0;
		left: 0;
		z-index: 999;
	}
	.aui-loading.aui-loading-ring .aui-loading-main{
		width: auto;
		height: auto;
		min-width: 55px;
		min-height: 55px;
		background: rgba(0,0,0,.8);
		border-radius: 10px;
		box-shadow: 0 0 1px rgba(100,100,100,.5);
		padding: 15px;
		box-sizing: border-box;
		-ms-animation: aui-fade-in .1s ease-out forwards;
		-webkit-animation: aui-fade-in .1s ease-out forwards;
		animation: aui-fade-in .1s ease-out forwards;
		position: absolute;
		top: 50%;
		left: 50%;
		z-index: 999;
		-ms-transform: translate(-50%, -50%);
		-webkit-transform: translate(-50%, -50%);
		transform: translate(-50%, -50%);
	}
	.aui-loading.aui-loading-ring .aui-loading-animate{
		width: 25px;
		height: 25px;
		margin: 0 auto;
		border-radius: 50%;
		position: relative;
		z-index: 999;
	}
	.aui-loading.aui-loading-ring .aui-loading-msg{
		width: 100%;
		height: 17px;
		max-width: -webkit-calc(100vw - 40px);
		max-width: calc(100vw - 40px);
		line-height: 17px;
		margin: 7px auto 0 auto;
		font-size: 13px;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
		color: #FFF;
		text-align: center;
		opacity: .9;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span{
		width: -webkit-calc(100% - 6px);
		width: calc(100% - 6px);
		height: 2px;
		display: inline-block;
		border-radius: 2px;
		position: absolute;
		box-sizing: initial !important;
		top: -webkit-calc(50% - 1px);
		top: calc(50% - 1px);
		left: 0;
		opacity: 0.3;
		-ms-animation: load-button 0.6s ease infinite;
		-webkit-animation: load-button 0.6s ease infinite;
		animation: load-button 0.6s ease infinite;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(1){
		border-left: 6px solid #FFF;
		-ms-transform: rotate(0deg);
		-webkit-transform: rotate(0deg);
		transform: rotate(0deg);
		-ms-animation-delay: 0.05s;
		-webkit-animation-delay: 0.05s;
		animation-delay: 0.05s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(2){
		border-left: 6px solid #FFF;
		-ms-transform: rotate(30deg);
		-webkit-transform: rotate(30deg);
		transform: rotate(30deg);
		-ms-animation-delay: 0.1s;
		-webkit-animation-delay: 0.1s;
		animation-delay: 0.1s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(3){
		border-left: 6px solid #FFF;
		-ms-transform: rotate(60deg);
		-webkit-transform: rotate(60deg);
		transform: rotate(60deg);
		-ms-animation-delay: 0.15s;
		-webkit-animation-delay: 0.15s;
		animation-delay: 0.15s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(4){
		border-left: 6px solid #FFF;
		-ms-transform: rotate(90deg);
		-webkit-transform: rotate(90deg);
		transform: rotate(90deg);
		-ms-animation-delay: 0.2s;
		-webkit-animation-delay: 0.2s;
		animation-delay: 0.2s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(5){
		border-left: 6px solid #FFF;
		-ms-transform: rotate(120deg);
		-webkit-transform: rotate(120deg);
		transform: rotate(120deg);
		-ms-animation-delay: 0.25s;
		-webkit-animation-delay: 0.25s;
		animation-delay: 0.25s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(6){
		border-left: 6px solid #FFF;
		-ms-transform: rotate(150deg);
		-webkit-transform: rotate(150deg);
		transform: rotate(150deg);
		-ms-animation-delay: 0.3s;
		-webkit-animation-delay: 0.3s;
		animation-delay: 0.3s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(7){
		border-right: 6px solid #FFF;
		-ms-transform: rotate(0deg);
		-webkit-transform: rotate(0deg);
		transform: rotate(0deg);
		-ms-animation-delay: 0.35s;
		-webkit-animation-delay: 0.35s;
		animation-delay: 0.35s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(8){
		border-right: 6px solid #FFF;
		-ms-transform: rotate(30deg);
		-webkit-transform: rotate(30deg);
		transform: rotate(30deg);
		-ms-animation-delay: 0.4s;
		-webkit-animation-delay: 0.4s;
		animation-delay: 0.4s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(9){
		border-right: 6px solid #FFF;
		-ms-transform: rotate(60deg);
		-webkit-transform: rotate(60deg);
		transform: rotate(60deg);
		-ms-animation-delay: 0.45s;
		-webkit-animation-delay: 0.45s;
		animation-delay: 0.45s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(10){
		border-right: 6px solid #FFF;
		-ms-transform: rotate(90deg);
		-webkit-transform: rotate(90deg);
		transform: rotate(90deg);
		-ms-animation-delay: 0.5s;
		-webkit-animation-delay: 0.5s;
		animation-delay: 0.5s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(11){
		border-right: 6px solid #FFF;
		-ms-transform: rotate(120deg);
		-webkit-transform: rotate(120deg);
		transform: rotate(120deg);
		-ms-animation-delay: 0.55s;
		-webkit-animation-delay: 0.55s;
		animation-delay: 0.55s;
	}
	.aui-loading.aui-loading-ring .aui-loading-animate .span:nth-child(12){
		border-right: 6px solid #FFF;
		-ms-transform: rotate(150deg);
		-webkit-transform: rotate(150deg);
		transform: rotate(150deg);
		-ms-animation-delay: 0.6s;
		-webkit-animation-delay: 0.6s;
		animation-delay: 0.6s;
	}
	/* 圆点放大缩小动画(全屏首次加载过度动画) */
	.aui-loading.aui-loading-dots{background-color: #FFF; height: 100%; width: 100%; position: fixed; z-index: 996; margin-top: 0px; top: 0px;}
	.aui-loading.aui-loading-dots .aui-loading-main{width: 100%;height: 100%;position: relative;}
	.aui-loading.aui-loading-dots .aui-loading-dot-items {position: absolute;left: 50%;top: 50%;height: 120px;width: 120px; text-align: center; margin-top: -60px;margin-left: -60px;}
	.aui-loading.aui-loading-dots .aui-loading-dot-item{width: 10px;height: 10px; background-color: #ec2b45; display: inline-block; margin-right: 6px; margin-top: 20px; border-radius: 2px; transform: scale(1) skewX(-30deg);}
	.aui-loading.aui-loading-dots #dot_one {-webkit-animation: dot_one 1.5s infinite; animation: dot_one 1.5s infinite;}
	.aui-loading.aui-loading-dots #dot_two {-webkit-animation: dot_two 1.5s infinite; animation: dot_two 1.5s infinite; -webkit-animation-delay: 0.2s; animation-delay: 0.2s;}
	.aui-loading.aui-loading-dots #dot_three {margin-right: 0; -webkit-animation: dot_three 1.5s infinite; animation: dot_three 1.5s infinite; -webkit-animation-delay: 0.4s; animation-delay: 0.4s;}
	@-webkit-keyframes dot_one {
		75% {-webkit-transform: scale(0) skewX(-30deg); }
	}
	@keyframes dot_one {
		75% {transform: scale(0) skewX(-30deg); -webkit-transform: scale(0) skewX(-30deg);}
	}
	@-webkit-keyframes dot_two {
		 75% {-webkit-transform: scale(0) skewX(-30deg); }
	}
	@keyframes dot_two {
		75% {transform: scale(0) skewX(-30deg); -webkit-transform:  scale(0) skewX(-30deg);}
	}
	@-webkit-keyframes dot_three {
		75% {-webkit-transform: scale(0) skewX(-30deg); }
	}
	@keyframes dot_three {
		75% {transform: scale(0) skewX(-30deg);-webkit-transform: scale(0) skewX(-30deg);} 
	}
	/* loading加载弹窗 load-button 动画 */
	@-ms-keyframes load-button {
		0% {opacity: 1;}
		100% {opacity: 0.3;}
	}
	@-webkit-keyframes load-button {
		0% {opacity: 1;}
		100% {opacity: 0.3;}
	}
	@keyframes load-button {
		0% {opacity: 1;}
		100% {opacity: 0.3;}
	}
	/* fade-in */
	@-ms-keyframes aui-fade-in{
		0%{opacity: 0;}
		100%{opacity: 1;}
	}
	@-webkit-keyframes aui-fade-in{
		0%{opacity: 0;}
		100%{opacity: 1;}
	}
	@keyframes aui-fade-in{
		0%{opacity: 0;}
		100%{opacity: 1;}
	}
</style>
