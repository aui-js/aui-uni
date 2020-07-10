<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="Badge数字角标" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="content-top">
				Badge数字角标通常用来标记重要信息，如接收到新消息、有未读消息等。
			</view>
			<view class="aui-card">
				<view class="aui-card-title"><text class="aui-card-title-line"></text>实心数字角标</view>
				<view class="aui-card-main">
					<text class="aui-badge" data-bg="gray">1</text>
					<text class="aui-badge" data-bg="blue">2</text>
					<text class="aui-badge" data-bg="success">33</text>
					<text class="aui-badge" data-bg="waring">44</text>
					<text class="aui-badge" data-bg="error">123</text>
				</view>
			</view>
			<view class="aui-card">
				<view class="aui-card-title"><text class="aui-card-title-line"></text>空心数字角标</view>
				<view class="aui-card-main">
					<text class="aui-badge aui-badge-nobg" data-bg="gray">1</text>
					<text class="aui-badge aui-badge-nobg" data-bg="blue">2</text>
					<text class="aui-badge aui-badge-nobg" data-bg="success">33</text>
					<text class="aui-badge aui-badge-nobg" data-bg="waring">44</text>
					<text class="aui-badge aui-badge-nobg" data-bg="error">123</text>
				</view>
			</view>
			<view class="aui-card">
				<view class="aui-card-title"><text class="aui-card-title-line"></text>迷你数字角标</view>
				<view class="aui-card-main">
					<text class="aui-badge aui-badge-small" data-bg="gray">1</text>
					<text class="aui-badge aui-badge-nobg aui-badge-small" data-bg="blue">2</text>
					<text class="aui-badge aui-badge-small" data-bg="success">33</text>
					<text class="aui-badge aui-badge-nobg aui-badge-small" data-bg="waring">44</text>
					<text class="aui-badge aui-badge-small" data-bg="error">123</text>
				</view>
			</view>
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
	.content-top{width: 100%; background: #f4f4f4; line-height: 25px; padding: 20px 15px; box-sizing: border-box; font-size: 14px; color: #aaa;}
	.list{width: -webkit-calc((100% - 40px) / 4); width: calc((100% - 40px) / 4); text-align: center; padding: 10px; box-sizing: border-box; display: inline-block; vertical-align: top; margin: 0px 5px; border-radius: 5px;}
	.list-title{width: 100%; height: 40px; line-height: 40px; font-size: 15px; padding-left: 12px; box-sizing: border-box; color: #333; position: relative;}
	.list-title::before{content: ''; width: 3px; height: 14px; background: #03A9F4; border-radius: 5px; position: absolute; top: 13px; left: 0;}
	.list text:first-child{font-size: 14px; color: #FFF; display: block;}
	.list text:last-child{font-size: 12px; color: #FFF;}
</style>
