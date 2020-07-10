<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="toast消息提示弹窗" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="aui-btn aui-btn-blue" @click.stop="showToast($event)">显示底部toast消息提示</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showToast($event)" data-location="middle">显示页面中心位置的toast消息提示</view>
			<!-- #ifdef APP-PLUS || H5 -->
			<view class="aui-btn aui-btn-blue" @click.stop="showToast($event)" data-icon="static/success.png" data-msg="操作成功">显示带图标垂直布局消息提示</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showToast($event)" data-icon="static/success.png" data-msg="操作成功" data-direction="row">显示带图标水平布局消息提示</view>	
			<!-- #endif -->
			<!-- #ifdef MP -->
			<view class="aui-btn aui-btn-blue" @click.stop="showToast($event)" data-icon="../../static/success.png" data-msg="操作成功">显示带图标垂直布局消息提示</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showToast($event)" data-icon="../../static/success.png" data-msg="操作成功" data-direction="row">显示带图标水平布局消息提示</view>		
			<!-- #endif -->
			
		</view>
		<aui-toast
			ref="toast"
			:msg="auiToast.msg"
			:location = "auiToast.location"
			:direction="auiToast.direction"
			:icon="auiToast.icon"
			:duration="auiToast.duration"
		></aui-toast>
	</view>
</template>

<script>
	import {aui} from '@/common/aui/js/aui.js';
	import auiHeader from '@/components/aui-header/aui-header.vue';
	import auiToast from '@/components/aui-toast/aui-toast.vue';
	export default {
		components: {
			auiHeader,
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
			//显示toast消息提示弹窗
			showToast(e){
				var _this = this;
				aui.isDefine(e.currentTarget.dataset.msg) ? _this.auiToast.msg = e.currentTarget.dataset.msg : _this.auiToast.msg = '网络连接错误，请稍后再试';
				aui.isDefine(e.currentTarget.dataset.icon) ? _this.auiToast.icon = e.currentTarget.dataset.icon : _this.auiToast.icon = '';
				aui.isDefine(e.currentTarget.dataset.location) ? _this.auiToast.location = e.currentTarget.dataset.location : _this.auiToast.location = 'bottom';
				aui.isDefine(e.currentTarget.dataset.direction) ? _this.auiToast.direction = e.currentTarget.dataset.direction : _this.auiToast.direction = 'col';
				// _this.$refs.toast.show();
				_this.$refs.toast.show().then(function(){
					console.log('toast关闭');
				});
			}
		}
	}
</script>

<style>
	.aui-content{padding: 15px 0 0 0;}
</style>
