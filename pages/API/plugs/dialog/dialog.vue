<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="dialog模态弹窗" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="aui-list-title">1、大按钮风格</view>
			<view class="aui-btn aui-btn-blue dialog-0" @click.stop="alert(1)">alert单按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-1" @click.stop="confirm(1)">confirm双按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-2" @click.stop="Delete(1)">delete删除提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-3">prompt输入弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-4">自定义带图标提示弹窗</view>
			<view class="aui-list-title">2、小按钮风格</view>
			<view class="aui-btn aui-btn-blue dialog-5" @click.stop="alert(2)">alert单按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-6" @click.stop="confirm(2)">confirm双按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-7" @click.stop="Delete(2)">delete删除提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-8">prompt输入弹窗</view>
			<view class="aui-list-title">3、两个以上按钮</view>
			<view class="aui-btn aui-btn-blue dialog-9">多按钮弹窗</view>
		</view>
		<aui-toast
			ref="toast"
			:msg="auiToast.msg"
			:location = "auiToast.location"
			:direction="auiToast.direction"
			:icon="auiToast.icon"
			:duration="auiToast.duration"
		></aui-toast>
		<aui-dialog 
			ref="auiDialog"
			:title="auiDialog.title"
			:msg="auiDialog.msg"
			:btns="auiDialog.btns"
			:mask="auiDialog.mask"
			:maskTapClose="auiDialog.maskTapClose"
			:theme="auiDialog.theme"
			@callback="dialogCallback"
		></aui-dialog>
	</view>
</template>

<script>
	import {aui} from '@/common/aui/js/aui.js';
	import auiHeader from '@/components/aui-header/aui-header.vue';
	import auiToast from '@/components/aui-toast/aui-toast.vue';
	import auiDialog from '@/components/aui-dialog/aui-dialog.vue';
	export default {
		components: {
			auiHeader,
			auiDialog,
			auiToast
		},
		data() {
			return {
				contentHeight: null,
				auiToast: {
					msg: '网络连接错误，请稍后再试',
					icon: '',
					location: 'bottom',
					direction: 'col',
					duration: 2000,
				},
				auiDialog: {
					title: '提示',
					msg: "提示内容",
					btns: [
						{name: '取消', color: '#909090'},
						{name: '确定', color: '#197DE0'}
					],
					mask: true,
					maskTapClose: true,
					theme: 1,
				},
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
			alert(theme){
				var _this = this;
				_this.auiDialog.title = '提示';
				_this.auiDialog.msg = '您点击了alert单按钮模态弹窗！';
				_this.auiDialog.btns = [{name: '确定', color: '#197DE0'}];
				_this.auiDialog.theme = theme;
				_this.$refs.auiDialog.show();
			},
			confirm(theme){
				var _this = this;
				_this.auiDialog.title = '提示';
				_this.auiDialog.msg = '您点击了confirm双按钮模态弹窗！';
				_this.auiDialog.btns = [
					{name: '取消'},
					{name: '确定'}
				];
				_this.auiDialog.theme = theme;
				_this.$refs.auiDialog.show();
			},
			Delete(theme){
				var _this = this;
				_this.auiDialog.title = '提示';
				_this.auiDialog.msg = '您点击了delete删除模态弹窗！';
				_this.auiDialog.btns = [
					{name: '取消'},
					{name: '删除'}
				];
				_this.auiDialog.theme = theme;
				_this.$refs.auiDialog.show();
			},
			dialogCallback(e){
				var _this = this;
				console.log(e);
				if(e.msg=='确定' || e.msg == '删除'){
					_this.auiToast.msg = _this.auiDialog.msg;
					_this.$refs.toast.show().then(function(){
						console.log('toast关闭');
					});
				}
			}
		}
	}
</script>

<style>
	
</style>
