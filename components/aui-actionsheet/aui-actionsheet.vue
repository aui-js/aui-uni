<template name="aui-actionsheet">
	<view class="aui-actionsheet" v-if="SHOW" :class="{
		'aui-actionsheet-bottom': location=='bottom', 
		'aui-actionsheet-middle': location=='middle',
		'aui-actionsheet-style-1': Number(theme)==1,
		'aui-actionsheet-style-2': Number(theme)==2,
		'aui-actionsheet-in': FADE==1,
		'aui-actionsheet-out': FADE==0}"
	>
		<view class="aui-mask" v-if="mask" @click.stop="maskTapClose ? hide() : ''"></view>
		<view class="aui-actionsheet-main">
			<view class="aui-actionsheet-title" v-if="title">{{title}}</view>
			<view class="aui-actionsheet-items">
				<view class="aui-actionsheet-item" v-for="(item, index) in items" :key="index" :data-index="index + 1" 
					:style="{
						'color': touchIndex == index + 1 ? touchStyle.color : item.color,
						'fontSize': item.fontSize,
						'textAlign': item.textAlign,
						'background': touchIndex == index + 1 ? touchStyle.background : ''
					}"
					@click.stop="_btnTab($event)"
					@touchstart="_btnTouchStart($event)"
					@touchmove="_btnTouchEnd($event)"
					@touchend="_btnTouchEnd($event)"
				>{{item.name}}</view>
			</view>
			<view class="aui-actionsheet-cancle" data-index="0" v-if="cancel"
				:style="{
					'color': touchIndex == 0 ? touchStyle.color : '',
					'background': touchIndex == 0 ? touchStyle.background : ''
				}"
				@click.stop="_btnTab($event)"
				@touchstart="_btnTouchStart($event)"
				@touchmove="_btnTouchEnd($event)"
				@touchend="_btnTouchEnd($event)"
			>{{cancel}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'aui-actionsheet',
		props: {
			title: { //标题
				type: String,
				default: ''
			},
			mask: { //是否显示遮罩，默认false
				type: Boolean,
				default: true
			},
			maskTapClose: { //遮罩层点击是否关闭
				type: Boolean,
				default: true
			},
			items: {
				type: Array,
				default (){
					return [
						{name: "", color: "", fontSize: "", textAlign: ""}
					]
				}
			},
			cancel: {
				type: String,
				default: ''
			},
			location: { //位置 <1、bottom:位于底部，从底部弹出显示>、<2、middle:位于页面中心位置>
				type: String,
				default: 'bottom'
			},
			theme: { //主题样式，控制模态弹窗按钮显示风格
				type: Number,
				default: 1
			},
		},
		data() {
			return {
				SHOW: false,
				FADE: -1,
				touchIndex: -1, //长按时当前索引
				touchStyle: { //长按时当前样式设置
					color: '',
					background: '#EFEFEF'
				}
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
					var data = {
						status: 0,
						msg: index != 0 ? _this.items[index - 1].name : _this.cancel,
						index: index
					};
					_this.$emit("callback", data);
					clearTimeout(_closetimer);
				},100)
			},
			_btnTouchStart(e){
				var _this = this,
					index = Number(e.currentTarget.dataset.index);
				_this.touchIndex = index;
			},
			_btnTouchEnd(e){
				var _this = this,
					index = Number(e.currentTarget.dataset.index);
				_this.touchIndex = -1;	
			},		
		}
	}
</script>

<style>
	/* actionSheet 操作表样式 */
	.aui-actionsheet{
		width: 100vw;
		height: 100vh;
		opacity: 0;
		-ms-animation: aui-fade-in .1s ease-out forwards;
		-webkit-animation: aui-fade-in .1s ease-out forwards;
		animation: aui-fade-in .1s ease-out forwards;
		position: fixed;
		top: 0;
		left: 0;
		z-index: 999;
	}
	.aui-actionsheet.aui-actionsheet-style-1 .aui-actionsheet-main{
		width: -webkit-calc(100vw - 20px);
		width: calc(100vw - 20px);
		max-height: 60vh;
		overflow: hidden;
		border-radius: 10px;
		position: absolute;
		left: 10px;
		z-index: 999;
	}
	.aui-actionsheet.aui-actionsheet-style-2 .aui-actionsheet-main{
		width: 100%;
		max-height: 60vh;
		overflow: hidden;
		position: absolute;
		left: 0px;
		z-index: 999;
	}
	.aui-actionsheet .aui-actionsheet-title{
		width: 100%;
		min-height: 50px;
		line-height: 25px;
		padding: 12px 10px;
		text-align: center;
		color: #909090;
		box-sizing: border-box;
		font-size: 15px;
		/*font-weight: bolder;*/
		background: #FFF;
		position: relative;
	}
	.aui-actionsheet .aui-actionsheet-title:after{
		content: '';
		width: 100%;
		height: 1px;
		-ms-transform: scaleY(.3);
		-webkit-transform: scaleY(.3);
		transform: scaleY(.3);
		background: rgba(100,100,100,.3);
		position: absolute;
		bottom: 0;
		left: 0;
		z-index: 1;
	}
	.aui-actionsheet.aui-actionsheet-style-1.aui-actionsheet-bottom .aui-actionsheet-main{
		bottom: -40vh;
	}	
	.aui-actionsheet.aui-actionsheet-style-1.aui-actionsheet-bottom.aui-actionsheet-in .aui-actionsheet-main{
		-ms-animation: aui-slide-up .2s ease-out forwards;
		-webkit-animation: aui-slide-up .2s ease-out forwards;
		animation: aui-slide-up .2s ease-out forwards;		
	}
	.aui-actionsheet.aui-actionsheet-style-1.aui-actionsheet-bottom.aui-actionsheet-out .aui-actionsheet-main{
		-ms-animation: aui-slide-down .2s ease-out forwards;
		-webkit-animation: aui-slide-down .2s ease-out forwards;
		animation: aui-slide-down .2s ease-out forwards;		
	}
	.aui-actionsheet.aui-actionsheet-middle .aui-actionsheet-main{
		width: 80%;
		background: #FFF;
		top: 50%;
		left: 50%;
		webkit-transform: translate(-50%, -50%) scale(1.16);
		transform: translate(-50%, -50%) scale(1.16);	
		opacity: 0;
	}
	.aui-actionsheet.aui-actionsheet-middle.aui-actionsheet-in .aui-actionsheet-main{
		-ms-animation: aui-scale-in-tosmall-dialog .2s ease-out forwards;
		-webkit-animation: aui-scale-in-tosmall-dialog .2s ease-out forwards;
		animation: aui-scale-in-tosmall-dialog .2s ease-out forwards;
	}
	.aui-actionsheet.aui-actionsheet-middle.aui-actionsheet-out .aui-actionsheet-main{
		-ms-animation: aui-scale-out-tosmall-dialog .2s ease-out forwards;
		-webkit-animation: aui-scale-out-tosmall-dialog .2s ease-out forwards;
		animation: aui-scale-out-tosmall-dialog .2s ease-out forwards;
	}
	.aui-actionsheet.aui-actionsheet-style-2.aui-actionsheet-middle .aui-actionsheet-main{
		width: 80%;
		border-radius: 10px;
		background: #FFF;		
	}
	.aui-actionsheet.aui-actionsheet-style-2.aui-actionsheet-bottom .aui-actionsheet-main{
		bottom: -30vh;
		background: #FFF;
		border-radius: 10px 10px 0 0;		
	}
	.aui-actionsheet.aui-actionsheet-style-2.aui-actionsheet-bottom.aui-actionsheet-in .aui-actionsheet-main{
		-ms-animation: aui-slide-up-screen .2s ease-out forwards;
		-webkit-animation: aui-slide-up-screen .2s ease-out forwards;
		animation: aui-slide-up-screen .2s ease-out forwards;
	}
	.aui-actionsheet.aui-actionsheet-style-2.aui-actionsheet-bottom.aui-actionsheet-out .aui-actionsheet-main{
		-ms-animation: aui-slide-down-screen .2s ease-out forwards;
		-webkit-animation: aui-slide-down-screen .2s ease-out forwards;
		animation: aui-slide-down-screen .2s ease-out forwards;
	}
	.aui-actionsheet.aui-actionsheet-style-1 .aui-actionsheet-items{
		width: 100%;
		font-size: 0;
		background: #FFF;
		border-bottom-left-radius: 7px;
		border-bottom-right-radius: 7px;
	}
	.aui-actionsheet.aui-actionsheet-style-2 .aui-actionsheet-items{
		width: 100%;
		background: #FFF;
		font-size: 0;
	}
	.aui-actionsheet .aui-actionsheet-item{
		width: 100%;
		height: 50px;
		line-height: 50px;
		font-size: 17px;
		padding: 0 20px;
		box-sizing: border-box;
		color: #333;
		background: #FFF;
		text-align: center;
		position: relative;
		vertical-align: top;
	}
	.aui-actionsheet.aui-actionsheet-style-1 .aui-actionsheet-item:first-child{
		border-top-left-radius: 10px;
		border-top-right-radius: 10px;
	}
	.aui-actionsheet.aui-actionsheet-style-1 .aui-actionsheet-item:last-child{
		border-bottom-left-radius: 10px;
		border-bottom-right-radius: 10px;
	}
	.aui-actionsheet .aui-actionsheet-item:after{
		content: '';
		width: 100%;
		height: 1px;
		-ms-transform: scaleY(.3);
		-webkit-transform: scaleY(.3);
		transform: scaleY(.3);
		background: rgba(100,100,100,.3);
		position: absolute;
		bottom: 0;
		left: 0;
		z-index: 1;
	}
	.aui-actionsheet.aui-actionsheet-style-1.aui-actionsheet-bottom .aui-actionsheet-item:last-child:after{
		display: none;
	}
	.aui-actionsheet .aui-actionsheet-cancle{
		width: 100%;
		height: 50px;
		line-height: 50px;
		font-size: 16px;
		color: #646464;
		text-align: center;
		background: #FFF;
	}
	.aui-actionsheet.aui-actionsheet-style-1.aui-actionsheet-bottom .aui-actionsheet-cancle{
		border-radius: 10px;
		margin-top: 10px;
	}
	.aui-actionsheet.aui-actionsheet-style-1.aui-actionsheet-middle .aui-actionsheet-cancle{
		border-bottom-left-radius: 10px;
		border-bottom-right-radius: 10px;
	}
</style>
