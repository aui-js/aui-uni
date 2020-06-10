<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="actionsheet操作弹窗" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<button class="aui-btn aui-btn-blue" @click.top="showActionsheet($event)" data-title="上传图片" data-location="bottom" data-theme="1" data-cancel="取消">底部弹出操作菜单（上传图片）</button>
			<button class="aui-btn aui-btn-blue" @click.top="showActionsheet($event)" data-title=" " data-location="middle" data-theme="2">页面中心弹出操作菜单（上传图片）</button>
			<button class="aui-btn aui-btn-blue" @click.top="showActionsheet($event)" data-title=" " data-location="bottom" data-theme="2" data-cancel="取消">底部弹出操作菜单(全屏宽度)</button>
		</view>
		<aui-toast
			ref="toast"
			:msg="auiToast.msg"
			:duration="auiToast.duration"
		></aui-toast>
		<aui-actionsheet
			ref="actionsheet"
			:title="auiActionsheet.title"
			:mask="auiActionsheet.mask"
			:maskTapClose="auiActionsheet.maskTapClose"
			:items="auiActionsheet.items"
			:location="auiActionsheet.location"
			:theme="auiActionsheet.theme"
			:cancel="auiActionsheet.cancel"
			@callback="actionsheetCallback"
		></aui-actionsheet>
		<!-- 简单调用actionsheet -->
		<!-- <aui-actionsheet
			ref="actionsheet"
			:items="auiActionsheet.items"
			@callback="actionsheetCallback"
		></aui-actionsheet> -->
	</view>
</template>

<script>
	import {aui} from '@/common/aui/js/aui.js';
	import auiHeader from '@/components/aui-header/aui-header.vue';
	import auiToast from '@/components/aui-toast/aui-toast.vue';
	import auiActionsheet from '@/components/aui-actionsheet/aui-actionsheet.vue';
	export default {
		components: {
			auiHeader,
			auiToast,
			auiActionsheet
		},
		data() {
			return {
				contentHeight: null,
				auiToast: {
					msg: '网络连接错误，请稍后再试',
					duration: 2000,
				},
				auiActionsheet: {
					title: '',
					mask: true,
					theme: 1,
					location: 'bottom',
					items: [
						{name: "拍照", color: "#333", fontSize: "16px", textAlign: "center"},
						{name: '从相册选择'}
					],
					cancel: '取消'
				}
			}
		},
		methods: {
			openWin(url, opts){
				aui.openWin(url, opts)
			},
			closeWin(){
				aui.closeWin()
			},
			headerHeight(e){
				//console.log(e);
				const { windowWidth, windowHeight } = uni.getSystemInfoSync();
				// #ifdef APP-PLUS
					this.contentHeight = windowHeight - e + 'px';				
				// #endif
			},
			showActionsheet(e){
				var _this = this;
				aui.isDefine(e.currentTarget.dataset.title) ? _this.auiActionsheet.title = e.currentTarget.dataset.title : _this.auiActionsheet.title = '';
				aui.isDefine(e.currentTarget.dataset.location) ? _this.auiActionsheet.location = e.currentTarget.dataset.location : _this.auiActionsheet.location = 'bottom';
				aui.isDefine(e.currentTarget.dataset.theme) ? _this.auiActionsheet.theme = Number(e.currentTarget.dataset.theme) : _this.auiActionsheet.theme = 1;
				aui.isDefine(e.currentTarget.dataset.cancel) ? _this.auiActionsheet.cancel = e.currentTarget.dataset.cancel : _this.auiActionsheet.cancel = '';
				_this.$refs.actionsheet.show();
			},
			actionsheetCallback(e){
				var _this = this;
				console.log(e);
				_this.auiToast.msg = '您点击了' + e.msg;
				_this.$refs.toast.show();	
			}
		}
	}
</script>

<style>
	.aui-content{padding: 15px 0 0 0;}
</style>
