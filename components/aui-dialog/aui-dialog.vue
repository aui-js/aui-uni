<template name="aui-dialog">
	<view class="aui-dialog" v-if="SHOW" :class="{'aui-dialog-in': FADE, 'aui-dialog-out': !FADE}">
		<view class="aui-mask" v-if="mask" @click.stop="maskTapClose ? hide() : ''"></view>
		<view class="aui-dialog-main" :class="{'aui-dialog-main-style-1': theme==1, 'aui-dialog-main-style-2': theme==2, 'aui-dialog-main-style-3': theme==3}">
			<view class="aui-dialog-title" v-if="title">{{title}}</view>
			<view class="aui-dialog-content">{{msg}}</view>
			<view class="aui-dialog-down">
				<view 
					class="aui-dialog-down-btn"
					v-for="(item, index) in btns" 
					:class="{'aui-dialog-down-cancel-btn': item.name=='取消', 'aui-dialog-down-delete-btn': item.name=='删除', 'active': BTNS[index].isTouch}"
					:key="index" 
					:data-index="index" 
					:style="{color: item.color, width: theme==1||theme==3?'calc(100% / '+ btns.length +')':''}"
					@click.stop="btnTab($event)"
					@touchstart="btnTouchStart($event)"
					@touchmove="btnTouchEnd($event)"
					@touchend="btnTouchEnd($event)"
				>{{item.name}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "aui-dialog",
		props: {
			title: { //标题
				type: String,
				default: ''
			},
			msg: { //描述内容
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
			btns: { //横向("row")或纵向("col")控制，默认纵向
				type: Array,
				default (){
					return [
						{name: '确定', color: '#909090', isTouch: false}
					]
				}
			},
			items: {
				type: Array,
				default (){
					return [
						{label: '', type: 'text', value: '(可选)', placeholder: ''}
					]
				}
			},
			theme: { //主题样式，控制模态弹窗按钮显示风格
				type: Number,
				default: 1
			},
			styles: { //样式
				type: Object,
				default () {
					return {
						w: '', //模态窗宽度，默认80%
						h: '', //模态窗高度，默认"auto"自适应
						bg: '',//模态窗背景色，默认白色
						textAlign: '', //模态窗内容排版
						zIndex: '', //模态窗层级
						title: {
							bg: "",
							color: "",
							lineHeight: "",
							textAlign: "",
							fontSize: "",
							padding: ""
						}
					}
				}
			},
		},
		data() {
			return {
				SHOW: false,
				FADE: false,
				BTNS: []
			};
		},
		created(){
			var _this = this;
			_this.BTNS = _this.btns;
			_this.BTNS.forEach((item, index)=>{
				_this.$set(item, 'isTouch', false)
			})
		},
		onLoad(){
			
		},
		methods:{
			//显示
			show(){
				var _this = this;
				return new Promise(function(resolve, reject){
					_this.SHOW = true;
					var _showtimer = setTimeout(()=>{
						_this.FADE = true;
						clearTimeout(_showtimer);
					},100)
					resolve();
				});
			},
			//隐藏
			hide(){
				var _this = this;
				return new Promise(function(resolve, reject){
					_this.FADE = false;
					var _hidetimer = setTimeout(()=>{
						_this.SHOW = false;
						clearTimeout(_hidetimer);
					},100)
					resolve();
				});
			},
			//底部按钮点击
			btnTab(e){
				var _this = this, 
					index = Number(e.currentTarget.dataset.index);
				_this.hide();
				var _closetimer = setTimeout(()=>{
					var data = {
						status: 0,
						msg: _this.btns[index].name,					
						index: index
					};
					_this.$emit("callback", data);
					clearTimeout(_closetimer);
				},100)
			},
			btnTouchStart(e){
				var _this = this,
					index = Number(e.currentTarget.dataset.index);
				_this.$set(_this.BTNS[index], 'isTouch', true)
			},
			btnTouchEnd(e){
				var _this = this,
					index = Number(e.currentTarget.dataset.index);
				_this.$set(_this.BTNS[index], 'isTouch', false)
			},
		}
	}
</script>

<style>
	/* dialog 模态弹窗样式 */
	.aui-dialog{
		width: 100vw;
		height: 100vh;
		opacity: 0;
		position: fixed;
		top: 0;
		left: 0;
		z-index: 999;
	}
	.aui-dialog-main{
		min-width: 300px;
		background: #fff;
		border-radius: 13px;
		position: absolute;
		top: 50%;
		left: 50%;
		-webkit-transition-property: -webkit-transform,opacity;
		transition-property: transform,opacity;
		-webkit-transform: translate3d(-50%,-50%,0) scale(1.185);
		transform: translate3d(-50%,-50%,0) scale(1.185);
		opacity: 0;
		z-index: 999;
	}
	.aui-dialog.aui-dialog-in{
		-webkit-transition-duration: 100ms;
		transition-duration: 100ms;
		opacity: 1;
	}
	.aui-dialog.aui-dialog-out{
		-webkit-transition-duration: 100ms;
		transition-duration: 100ms;
		opacity: 0;
	}
	.aui-dialog.aui-dialog-in .aui-mask{
		-webkit-transition-duration: 200ms;
		transition-duration: 200ms;
		opacity: 1;
	}
	.aui-dialog.aui-dialog-out .aui-mask{
		-webkit-transition-duration: 200ms;
		transition-duration: 200ms;
		opacity: 0;
	}
	.aui-dialog.aui-dialog-out .aui-dialog-main{
		-webkit-transition-duration: 200ms;
		transition-duration: 200ms;
		-webkit-transform: translate3d(-50%,-50%,0) scale(0.8);
		transform: translate3d(-50%,-50%,0) scale(0.8);
		opacity: 0
	}
	.aui-dialog.aui-dialog-in .aui-dialog-main{
		-webkit-transition-duration: 200ms;
		transition-duration: 200ms;
		-webkit-transform: translate3d(-50%,-50%,0) scale(1);
		transform: translate3d(-50%,-50%,0) scale(1);
		opacity: 1;
	}
	.aui-dialog-title{
		width: 100%;
		height: 40px;
		line-height: 55px;
		position: relative;
		font-size: 18px;
		/*font-weight: bolder;*/
		display: inline-block;
		border-top-left-radius: 13px;
		border-top-right-radius: 13px;
		text-align: center;
		color: #333;
		box-sizing: border-box;
	}
	.aui-dialog-content{
		width: 100%;
		max-height: 70vh;
		line-height: 27px;
		font-size: 16px;
		color: #555555;
		text-align: center;
		display: inline-block;
		overflow-y: scroll;
		padding: 30px 20px 25px 20px;
		box-sizing: border-box;
	}
	.aui-dialog-content::-webkit-scrollbar {
		width: 0px;
	}
	.aui-dialog-down{
		width: 100%;
		height: 50px;
		text-align: right;
		position: relative;
		overflow: hidden;
	}
	.aui-dialog-down-btn{
		width: auto;
		height: 100%;
		display: inline-block;
		font-size: 17px;
		color: #197DE0;
		text-align: center;
		position: relative;
	}
	.aui-dialog-down-btn.active{
		background: #EFEFEF;
	}
	.aui-dialog-down-cancel-btn{
		color: #909090;
	}
	.aui-dialog-down-delete-btn{
		color: #FF0000;
	}
	.aui-dialog-main-style-1 .aui-dialog-content{
		text-align: center;
	}
	.aui-dialog-main-style-1 .aui-dialog-down{
		height: 50px;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.aui-dialog-main-style-1 .aui-dialog-down-btn{
		line-height: 50px;
		display: flex;
		justify-content: center;
		align-items: center;
		flex: auto;
	}
	.aui-dialog-main-style-1 .aui-dialog-down:before{
		content: '';
		width: 100%;
		height: 1px;
		-ms-transform: scaleY(.3);
		-webkit-transform: scaleY(.3);
		transform: scaleY(.3);
		background: rgba(100,100,100,.3);
		position: absolute;
		top: 0;
		left: 0;
		z-index: 999;
	}
	.aui-dialog-main-style-1 .aui-dialog-down-btn:first-child{
		border-bottom-left-radius: 13px;
	}
	.aui-dialog-main-style-1 .aui-dialog-down-btn:last-child{
		border-bottom-right-radius: 13px;
	}
	.aui-dialog-main-style-1 .aui-dialog-down-btn:after{
		content: '';
		width: 1px;
		height: 100%;
		-ms-transform: scaleX(.3);
		-webkit-transform: scaleX(.3);
		transform: scaleX(.3);
		background: rgba(100,100,100,.3);
		position: absolute;
		top: 0;
		right: 0;
		z-index: 999;
	}
	.aui-dialog-main-style-1 .aui-dialog-down-btn:last-child:after{display: none;}
	.aui-dialog-main-style-2{
		border-radius: 6px;
	}
	.aui-dialog-main-style-2 .aui-dialog-title{
		padding: 0 15px;
		box-sizing: border-box;
	}
	.aui-dialog-main-style-2 .aui-dialog-down{
		height: 40px;
		padding: 0 10px 10px 10px;
		box-sizing: border-box;
	}
	.aui-dialog-main-style-2 .aui-dialog-down-btn{
		height: 30px;
		line-height: 30px;
		padding: 0 10px;
		margin: 0 0 0 10px;
	}
	.aui-dialog-main-style-3 .aui-dialog-down{
		height: auto;
	}
	.aui-dialog-main-style-3 .aui-dialog-down-btn:before{
		content: '';
		width: 100%;
		height: 1px;
		-ms-transform: scaleY(.3);
		-webkit-transform: scaleY(.3);
		transform: scaleY(.3);
		background: rgba(100,100,100,.4);
		position: absolute;
		bottom: 0;
		left: 0;
	}
	.aui-dialog-main-style-3 .aui-dialog-down-btn:last-child{
		border-bottom-left-radius: 13px;
		border-bottom-right-radius: 13px;
	}
	.aui-dialog-main-style-3 .aui-dialog-down-btn:last-child:before{display: none;}
	.aui-dialog-main-style-3 .aui-dialog-down-btn:first-child:after{display: none;}
</style>
