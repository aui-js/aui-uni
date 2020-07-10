<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="Button按钮" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<button class="aui-btn">页面主操作Normal</button>
			<button class="aui-btn aui-btn-load">页面主操作Loading</button>
			<button class="aui-btn aui-btn-disabled">页面主操作Disabled</button>
			<button class="aui-btn aui-btn-round">页面主操作Normal</button>
			<button class="aui-btn aui-btn-success">Success类操作Normal</button>
			<button class="aui-btn aui-btn-success aui-btn-disabled">Success类操作Disabled</button>
			<button class="aui-btn aui-btn-error">Error类操作Normal</button>
			<button class="aui-btn aui-btn-error aui-btn-disabled">Error类操作Disabled</button>
			<button class="aui-btn aui-btn-waring">警告类操作Normal</button>
			<button class="aui-btn aui-btn-waring aui-btn-disabled">警告类操作Disabled</button>
			<button class="aui-btn aui-btn-linear">线性按钮</button>
			<button class="aui-btn aui-btn-linear aui-btn-disabled">不可点击按钮</button>
			<button class="aui-btn aui-btn-linear aui-btn-medium">线性按钮</button>
			<button class="aui-btn aui-btn-linear aui-btn-disabled aui-btn-medium">不可点击按钮</button>
			<button class="aui-btn aui-btn-linear aui-btn-small">按钮</button>
			<button class="aui-btn aui-btn-linear aui-btn-disabled aui-btn-small">按钮</button>
		</view>
	</view>
</template>

<script>
	import {aui} from '@/common/aui/js/aui.js';
	import auiHeader from '@/components/aui-header/aui-header.vue';
	import {colorData} from '@/pages/ui/color/color.js';
	export default {
		components: {
			auiHeader
		},
		data() {
			return {
				contentHeight: null,
			}
		},
		mounted(){
			
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
			
		}
	}
</script>

<style>
	.aui-content{padding: 15px 0;}
	.list{width: -webkit-calc((100% - 40px) / 4); width: calc((100% - 40px) / 4); text-align: center; padding: 10px; box-sizing: border-box; display: inline-block; vertical-align: top; margin: 0px 5px; border-radius: 5px;}
	.list-title{width: 100%; height: 40px; line-height: 40px; font-size: 15px; padding-left: 12px; box-sizing: border-box; color: #333; position: relative;}
	.list-title::before{content: ''; width: 3px; height: 14px; background: #03A9F4; border-radius: 5px; position: absolute; top: 13px; left: 0;}
	.list text:first-child{font-size: 14px; color: #FFF; display: block;}
	.list text:last-child{font-size: 12px; color: #FFF;}
</style>
