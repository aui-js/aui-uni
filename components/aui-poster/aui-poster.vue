<template name="aui-poster">
	<view class="aui-poster" v-if="SHOW" :class="{
		'aui-poster-in': FADE==1,
		'aui-poster-out': FADE==0}"
	>
		<view class="aui-mask" v-if="mask" @click.stop="maskTapClose ? hide() : ''"></view>
		<view class="aui-poster-main">
			<img class="aui-poster-img" mode="widthFix" :src="image">
			<img class="aui-poster-close" mode="widthFix" @click.stop="_btnTab($event)" src="https://xbjz1.oss-cn-beijing.aliyuncs.com/upload/default/gz-close.png">
		</view>
	</view>
</template>

<script>
	export default {
		name: 'aui-poster',
		props: {			
			mask: { //是否显示遮罩，默认false
				type: Boolean,
				default: true
			},
			maskTapClose: { //遮罩层点击是否关闭
				type: Boolean,
				default: true
			},
			image: {
				type: String,
				default: ''
			},
		},
		data() {
			return {
				SHOW: false,
				FADE: -1
			};
		},
		created(){
			var _this = this;
				
		},
		onLoad(){
			
		},
		methods:{
			show(){
				var _this = this;
				return new Promise(function(resolve, reject){
					_this.SHOW = true;
					_this.FADE = 1;					
					resolve();
				});
			},
			hide(){
				var _this = this;
				return new Promise(function(resolve, reject){
					_this.FADE = 0;
					var _hidetimer = setTimeout(()=>{
						_this.SHOW = false;
						_this.FADE = -1;
						clearTimeout(_hidetimer);
					},100)
					resolve();
				});
			},
			_btnTab(e){
				var _this = this,
					index = Number(e.currentTarget.dataset.index);
				_this.hide();
				var _closetimer = setTimeout(()=>{
					_this.$emit("callback");
					clearTimeout(_closetimer);
				},100)
			},			
		}
	}
</script>

<style>
	/*poster 广告弹窗*/
	.aui-poster{width: 100vw; height: 100vh; position: fixed; top: 0; left: 0; z-index: 998;}
	.aui-poster .aui-mask{z-index: 996; position: absolute;}
	.aui-poster-main{width: 80%; opacity: 0; position: fixed; top: -50vh; left: 10%; z-index: 999;}
	.aui-poster-in .aui-poster-main{animation: aui-slide-up_to_middle .3s ease-out forwards;}
	.aui-poster-out .aui-poster-main{animation: aui-slide-middle_to_up .2s ease-out forwards;}
	.aui-poster-main .aui-poster-img{width: 100%; pointer-events: auto; position: relative; z-index: 999;}
	.aui-poster-main .aui-poster-close{width: 30px; position: absolute; top: -webkit-calc(100% - 10px); top: calc(100% - 10px); left: 50%; -moz-transform: translate(-50%,0); -ms-transform: translate(-50%,0); -webkit-transform: translate(-50%,0); transform: translate(-50%,0); z-index: 998;}
	
</style>
