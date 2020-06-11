<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="设备" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<button class="aui-btn aui-btn-blue btn-0">判断是否为微信浏览器</button>
			<button class="aui-btn aui-btn-blue btn-1">判断是否为IOS系统</button>
			<button class="aui-btn aui-btn-blue btn-2">判断是否为android系统</button>
			<button class="aui-btn aui-btn-blue btn-3">判断是否为IE浏览器</button>
			<button class="aui-btn aui-btn-blue btn-4">判断是否为PC</button>
			<button class="aui-btn aui-btn-blue btn-5">获取设备是否连接网络</button>
			<button class="aui-btn aui-btn-blue btn-6">获取设备网络类型</button>
		</view>
	</view>
</template>

<script>
	import {aui} from '@/common/aui/js/aui.js';
	import auiHeader from '@/components/aui-header/aui-header.vue';
	export default {
		components: {
			auiHeader
		},
		data() {
			return {
				contentHeight: null
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
			}
		}
	}
</script>

<style>
	.aui-content{padding-top: 15px;}
</style>
