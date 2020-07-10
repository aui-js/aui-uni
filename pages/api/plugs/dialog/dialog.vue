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
			<view class="aui-btn aui-btn-blue dialog-3" @click.stop="prompt(1)">prompt输入弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-4" @click.stop="confirmCustom(1)">自定义带图标提示弹窗</view>
			<view class="aui-list-title">2、小按钮风格</view>
			<view class="aui-btn aui-btn-blue dialog-5" @click.stop="alert(2)">alert单按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-6" @click.stop="confirm(2)">confirm双按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-7" @click.stop="Delete(2)">delete删除提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-8" @click.stop="prompt(2)">prompt输入弹窗</view>
			<view class="aui-list-title">3、两个以上按钮</view>
			<view class="aui-btn aui-btn-blue dialog-9" @click.stop="confirmMoreBtns(3)">多按钮弹窗</view>
			<view class="aui-list-title">3、带背景色按钮</view>
			<view class="aui-btn aui-btn-blue dialog-10" @click.stop="alert(4)">alert单按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-11" @click.stop="confirm(4)">confirm双按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-12" @click.stop="Delete(4)">delete删除提醒弹窗</view>
		</view>
		<aui-toast
			ref="toast"
			:msg="auiToast.msg"
			:duration="auiToast.duration"
		></aui-toast>
		<aui-dialog 
			ref="dialog"
			:title="auiDialog.title"
			:msg="auiDialog.msg"
			:btns="auiDialog.btns"
			:mask="auiDialog.mask"
			:maskTapClose="auiDialog.maskTapClose"
			:items="auiDialog.items"
			:theme="auiDialog.theme"
			@callback="dialogCallback"
		></aui-dialog>
		<!-- 简单调用dialog -->
		<!-- <aui-dialog
			ref="dialog"
			:title="auiDialog.title"
			:msg="auiDialog.msg"
			:btns="auiDialog.btns"
			:mask="auiDialog.mask"
			@callback="dialogCallback"
		></aui-dialog> -->
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
					duration: 2000,
				},
				auiDialog: {
					title: '',
					msg: '',
					btns: [{name: '确定'}],
					mask: true,
					maskTapClose: true,
					items: [],
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
			//dialog弹窗底部按钮回调
			dialogCallback(e){
				var _this = this;
				//console.log(e);
				_this.auiToast.msg = '您点击了' + e.msg;
				_this.$refs.toast.show();				
				if(_this.$refs.dialog.getVal().length > 0)
				{ //prompt输入框——点击确定时弹出输入内容
					_this.auiDialog.title = '提示';
					_this.$refs.dialog.getVal().forEach(function(item, index){
						_this.auiDialog.msg += '<div style="display: flex;">' + item.label + '：' + item.value + '</div>';
					});
					_this.auiDialog.btns = [{name: '确定', color: '#197DE0'}];
					_this.auiDialog.items = [];
					_this.auiDialog.theme = 1;
					_this.$refs.dialog.show();
				}
			},
			alert(theme){
				var _this = this;
				_this.auiDialog.title = '提示';
				_this.auiDialog.msg = '您点击了alert单按钮模态弹窗！';
				_this.auiDialog.btns = [{name: '确定', color: theme != 4 ? '#197DE0' :''}];
				_this.auiDialog.items = [];
				_this.auiDialog.theme = theme;
				_this.$refs.dialog.show();
			},
			confirm(theme){
				var _this = this;
				_this.auiDialog.title = '提示';
				_this.auiDialog.msg = '您点击了confirm双按钮模态弹窗！';
				_this.auiDialog.items = [];
				_this.auiDialog.btns = [
					{name: '取消'},
					{name: '确定'}
				];
				_this.auiDialog.theme = theme;
				_this.$refs.dialog.show();
			},
			Delete(theme){
				var _this = this;
				_this.auiDialog.title = '提示';
				_this.auiDialog.msg = '您点击了delete删除模态弹窗！';
				_this.auiDialog.items = [];
				_this.auiDialog.btns = [
					{name: '取消'},
					{name: '删除'}
				];
				_this.auiDialog.theme = theme;
				_this.$refs.dialog.show();
			},
			confirmCustom(theme){
				var _this = this;
				_this.auiDialog.title = '提示';
				_this.auiDialog.msg = '<div style="display: flex; justify-content: center; margin: 0 0 10px 0;"><img style="width: 100px; height: 100px; display: inline-block" src="http://pic2.sc.chinaz.com/files/pic/pic9/201910/bpic14122.jpg"></div><div style="width: 100%; display: block; text-align: center;">带图标模态弹窗</div>';
				_this.auiDialog.items = [];
				_this.auiDialog.btns = [
					{name: '取消'},
					{name: '确定'}
				];
				_this.auiDialog.theme = theme;
				_this.$refs.dialog.show();
			},
			confirmMoreBtns(theme){
				var _this = this;
				_this.auiDialog.title = '提示';
				_this.auiDialog.msg = '您点击了confirm双按钮模态弹窗！';
				_this.auiDialog.items = [];
				_this.auiDialog.btns = [
					{name: '残忍拒绝'},
					{name: '再逛逛'}, 
					{name: "返回首页", color: "#909090"}
				];
				_this.auiDialog.theme = theme;
				_this.$refs.dialog.show();
			},
			prompt(theme){
				var _this = this;
				_this.auiDialog.title = '提示';
				_this.auiDialog.msg = '';
				_this.auiDialog.items = [
					{label: '姓名', type: '', placeholder: '请输入姓名'},
					{label: '性别', type: 'text', placeholder: '请输入性别'}
				];
				_this.auiDialog.btns = [
					{name: '取消'},
					{name: '确定'}
				];
				_this.auiDialog.theme = theme;
				_this.$refs.dialog.show();
			},
		}
	}
</script>

<style>
	
</style>
