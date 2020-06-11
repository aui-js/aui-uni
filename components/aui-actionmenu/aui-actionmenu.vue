<template name="aui-actionmenu">
	<view class="aui-actionmenu" v-if="SHOW" :class="{
		'aui-actionmenu-bottom': location=='bottom', 
		'aui-actionmenu-middle': location=='middle',
		'aui-actionmenu-style-1': Number(theme)==1,
		'aui-actionmenu-style-2': Number(theme)==2,
		'aui-actionmenu-in': FADE==1,
		'aui-actionmenu-out': FADE==0}"
	>
		<view class="aui-mask" v-if="mask" @click.stop="maskTapClose ? hide() : ''"></view>
		<view class="aui-actionmenu-main">
			<view class="aui-actionmenu-title" v-if="title">{{title}}</view>
			<view class="aui-actionmenu-items" :style="{padding: !title ? '10px' : ''}">
				<view class="aui-actionmenu-item" v-for="(item, index) in items" :key="index" :data-index="index + 1" 
					:class="{'no-icon': !item.icon && !item.img}"
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
				>
					<img v-if="item.img" :src="item.img" alt="">
					<view class="iconfont" v-if="item.icon" :class="item.icon" :style="{color: item.iconColor}"></view>
					<view class="aui-actionmenu-item-text">{{item.name}}</view>
				</view>
			</view>
			<view class="aui-actionmenu-cancle" data-index="0"
				:style="{
					'color': touchIndex == 0 ? touchStyle.color : '',
					'background': touchIndex == 0 ? touchStyle.background : ''
				}"
				@click.stop="_btnTab($event)"
				@touchstart="_btnTouchStart($event)"
				@touchmove="_btnTouchEnd($event)"
				@touchend="_btnTouchEnd($event)"
			>{{cancel || '取消'}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'aui-actionmenu',
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
						{name: "", icon: "", iconColor: "", img: ""}
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
	/* actionmenu 操作表样式 */
	.aui-actionmenu{
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
	.aui-actionmenu.aui-actionmenu-style-1 .aui-actionmenu-main{
		width: -webkit-calc(100vw - 20px);
		width: calc(100vw - 20px);
		max-height: 60vh;
		overflow: hidden;
		border-radius: 10px;
		background: #FFF;	
		font-size: 0;
		position: absolute;	
		left: 10px;
		z-index: 999;
	}
	.aui-actionmenu.aui-actionmenu-style-2 .aui-actionmenu-main{
		width: 100%;	
		max-height: 60vh;
		overflow: hidden;
		font-size: 0;
		background: #FFF;
		border-radius: 10px 10px 0 0;
		position: absolute;	
		left: 0px;
		z-index: 999;
	}
	.aui-actionmenu .aui-actionmenu-title{
		width: 100%;
		min-height: 50px;
		line-height: 25px;
		padding: 12px 10px;
		text-align: center;
		color: #646464;
		box-sizing: border-box;
		font-size: 16px;
		font-weight: 500;
		background: #FFF;
		position: relative;
	}
	.aui-actionmenu .aui-actionmenu-title:before,.aui-actionmenu .aui-actionmenu-title:after{
		content: '';
		width: 40px;
		height: 1px;
		-moz-transform: scaleY(.3);
		-ms-transform: scaleY(.3);
		-webkit-transform: scaleY(.3);
		transform: scaleY(.3);
		background: rgba(100,100,100,.4);
		position: absolute;
		bottom: 50%;
		z-index: 1;
	}
	.aui-actionmenu .aui-actionmenu-title:before{
		left: 25%;
	}
	.aui-actionmenu .aui-actionmenu-title:after{
		right: 25%;
	}
	.aui-actionmenu.aui-actionmenu-style-1.aui-actionmenu-bottom .aui-actionmenu-main{
		bottom: -40vh;
	}	
	.aui-actionmenu.aui-actionmenu-style-1.aui-actionmenu-bottom.aui-actionmenu-in .aui-actionmenu-main{
		-ms-animation: aui-slide-up .2s ease-out forwards;
		-webkit-animation: aui-slide-up .2s ease-out forwards;
		animation: aui-slide-up .2s ease-out forwards;		
	}
	.aui-actionmenu.aui-actionmenu-style-1.aui-actionmenu-bottom.aui-actionmenu-out .aui-actionmenu-main{
		-ms-animation: aui-slide-down .2s ease-out forwards;
		-webkit-animation: aui-slide-down .2s ease-out forwards;
		animation: aui-slide-down .2s ease-out forwards;		
	}
	.aui-actionmenu.aui-actionmenu-middle .aui-actionmenu-main{
		width: 80%;
		background: #FFF;
		top: 50%;
		left: 50%;
		webkit-transform: translate(-50%, -50%) scale(1.16);
		transform: translate(-50%, -50%) scale(1.16);	
		opacity: 0;
	}
	.aui-actionmenu.aui-actionmenu-style-1.aui-actionmenu-middle .aui-actionmenu-main{
		width: -webkit-calc(100% - 30px);
		width: calc(100% - 30px);
	}
	.aui-actionmenu.aui-actionmenu-middle.aui-actionmenu-in .aui-actionmenu-main{
		-ms-animation: aui-scale-in-tosmall-dialog .2s ease-out forwards;
		-webkit-animation: aui-scale-in-tosmall-dialog .2s ease-out forwards;
		animation: aui-scale-in-tosmall-dialog .2s ease-out forwards;
	}
	.aui-actionmenu.aui-actionmenu-middle.aui-actionmenu-out .aui-actionmenu-main{
		-ms-animation: aui-scale-out-tosmall-dialog .2s ease-out forwards;
		-webkit-animation: aui-scale-out-tosmall-dialog .2s ease-out forwards;
		animation: aui-scale-out-tosmall-dialog .2s ease-out forwards;
	}
	.aui-actionmenu.aui-actionmenu-style-2.aui-actionmenu-middle .aui-actionmenu-main{
		width: 80%;
		border-radius: 10px;
		background: #FFF;		
	}
	.aui-actionmenu.aui-actionmenu-style-2.aui-actionmenu-bottom .aui-actionmenu-main{
		bottom: -30vh;
		background: #FFF;
		border-radius: 10px 10px 0 0;		
	}
	.aui-actionmenu.aui-actionmenu-style-2.aui-actionmenu-bottom.aui-actionmenu-in .aui-actionmenu-main{
		-ms-animation: aui-slide-up-screen .2s ease-out forwards;
		-webkit-animation: aui-slide-up-screen .2s ease-out forwards;
		animation: aui-slide-up-screen .2s ease-out forwards;
	}
	.aui-actionmenu.aui-actionmenu-style-2.aui-actionmenu-bottom.aui-actionmenu-out .aui-actionmenu-main{
		-ms-animation: aui-slide-down-screen .2s ease-out forwards;
		-webkit-animation: aui-slide-down-screen .2s ease-out forwards;
		animation: aui-slide-down-screen .2s ease-out forwards;
	}
	.aui-actionmenu.aui-actionmenu-style-1 .aui-actionmenu-items{
		width: 100%;
		padding: 0 10px 10px 10px;
		box-sizing: border-box;
	}
	.aui-actionmenu.aui-actionmenu-style-2 .aui-actionmenu-items{
		width: 100%;
		padding: 0 10px 10px 10px;
		box-sizing: border-box;
		font-size: 0;
	}
	.aui-actionmenu .aui-actionmenu-item{
		width: 25%;
		padding: 10px;
		box-sizing: border-box;
		color: #333;
		border-radius: 3px;
		background: #FFF;
		text-align: center;
		display: inline-block;
		vertical-align: top;
		position: relative;
	}
	.aui-actionmenu .aui-actionmenu-item img{
		width: 70%;
	}
	.aui-actionmenu .aui-actionmenu-item .iconfont{
		font-size: 50px;
		display: inline-block;
		margin-bottom: 5px;
	}
	.aui-actionmenu .aui-actionmenu-item .aui-actionmenu-item-text{
		width: 100%;
		line-height: 15px;
		font-size: 14px;
		color: #333;
		margin: 5px 0 0 0;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
	}
	.aui-actionmenu .aui-actionmenu-item.no-icon{
		width: 100%;
		height: 50px;
		line-height: 50px;
		padding: 0 25px 0 15px;
		box-sizing: border-box;
		font-size: 15px;
		text-align: left;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: inherit;
		color: #333;
		position: relative;
	}
	.aui-actionmenu .aui-actionmenu-item.no-icon .aui-actionmenu-item-text{
		width: 100%;
		line-height: 50px;
		margin: 0;
	}
	.aui-actionmenu .aui-actionmenu-cancle{
		width: 100%;
		height: 50px;
		line-height: 50px;
		font-size: 16px;
		color: #646464;
		text-align: center;
		background: #FFF;
		position: relative;
	}
	.aui-actionmenu.aui-actionmenu-style-1.aui-actionmenu-bottom .aui-actionmenu-cancle{	
		border-bottom-left-radius: 10px;
		border-bottom-right-radius: 10px;
	}
	.aui-actionmenu .aui-actionmenu-cancle:after{
		content: '';
		width: 100%;
		height: 1px;
		-moz-transform: scaleY(.3);
		-ms-transform: scaleY(.3);
		-webkit-transform: scaleY(.3);
		transform: scaleY(.3);
		background: rgba(100,100,100,.3);
		position: absolute;
		top: 0;
		left: 0;
		z-index: 1;
	}
	.aui-actionmenu.aui-actionmenu-middle .aui-actionmenu-cancle{
		width: 30px;
		height: 30px;
		font-size: 0;
		color: transparent;
		position: absolute;
		top: 10px;
		right: 5px;
	}
	.aui-actionmenu.aui-actionmenu-middle .aui-actionmenu-cancle::before{
		content: '';
		width: 15px;
		height: 1px;
		background: #909090;
		position: absolute;
		top: -webkit-calc((100% - 1px) / 2);
		top: calc((100% - 1px) / 2);
		left: 7.5px;
		-moz-transform: rotate(45deg);
		-ms-transform: rotate(45deg);
		-webkit-transform: rotate(45deg);
		transform: rotate(45deg);
	}
	.aui-actionmenu.aui-actionmenu-middle .aui-actionmenu-cancle:after{
		content: '';
		width: 15px;
		height: 1px;
		background: #909090;
		position: absolute;
		top: -webkit-calc((100% - 1px) / 2);
		top: calc((100% - 1px) / 2);
		left: 7.5px;
		-moz-transform: rotate(-45deg);
		-ms-transform: rotate(-45deg);
		-webkit-transform: rotate(-45deg);
		transform: rotate(-45deg);
	}
</style>
