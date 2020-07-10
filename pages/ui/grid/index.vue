<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="Grid九宫格" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="content-top">
				Grid九宫格组件主要使用场景如：商品分类列表、商品推荐列表、热门内容等。
			</view>
			<view class="aui-card">
				<view class="aui-card-title"><text class="aui-card-title-line"></text>3列</view>
				<view class="aui-card-main" style="padding: 0;">
					<!-- 九宫格组件 -->
					<view class="aui-grids">
						<view class="aui-grid" col="3">
							<view class="aui-grid-icon"><text class="iconfont iconindexlist" style="color: #05c091;"></text></view>
							<view class="aui-grid-text">Index索引列表</view>
						</view>
						<view class="aui-grid" col="3">
							<view class="aui-grid-icon"><text class="iconfont iconnavbar" style="color: #fe2f24;"></text></view>
							<view class="aui-grid-text">Navbar导航</view>
						</view>
						<view class="aui-grid" col="3">
							<view class="aui-grid-icon"><text class="iconfont iconnumberbox" style="font-size: 25px; color: #db639b;"></text></view>
							<view class="aui-grid-text">Number输入框</view>
						</view>
						<view class="aui-grid" col="3">
							<view class="aui-grid-icon"><text class="iconfont iconnotice" style="font-size: 25px; color: #fe6503;"></text></view>
							<view class="aui-grid-text">Notice通告栏</view>
						</view>
						<view class="aui-grid" col="3">
							<view class="aui-grid-icon"><text class="iconfont iconsearch" style="font-size: 22px; color: #197DE0;"></text></view>
							<view class="aui-grid-text">Searchbar搜索</view>
						</view>
						<view class="aui-grid" col="3">
							<view class="aui-grid-icon"><text class="iconfont iconxing" style="font-size: 22px; color: #fec002;"></text></view>
							<view class="aui-grid-text">Fav收藏按钮</view>
						</view>
						<view class="aui-grid" col="3">
							<view class="aui-grid-icon"><text class="iconfont iconclock" style="color: #EE0000;"></text></view>
							<view class="aui-grid-text">Countdown倒计时</view>
						</view>
						<view class="aui-grid" col="3">
							<view class="aui-grid-icon"><text class="iconfont iconheadlines" style="color: #add51d;"></text></view>
							<view class="aui-grid-text">Card卡片</view>
						</view>
						<view class="aui-grid" col="3">
							<view class="aui-grid-icon"><text class="iconfont iconzhedie" style="color: #05c091;"></text></view>
							<view class="aui-grid-text">Collapse折叠面板</view>
						</view>					
					</view>
				</view>
			</view>
			<view class="aui-card">
				<view class="aui-card-title"><text class="aui-card-title-line"></text>4列</view>
				<view class="aui-card-main" style="padding: 0;">
					<!-- 九宫格组件 -->
					<view class="aui-grids">
						<view class="aui-grid" col="4">
							<view class="aui-grid-icon"><text class="iconfont iconindexlist" style="color: #05c091;"></text></view>
							<view class="aui-grid-text">Index索引列表</view>
						</view>
						<view class="aui-grid" col="4">
							<view class="aui-grid-icon"><text class="iconfont iconnavbar" style="color: #fe2f24;"></text></view>
							<view class="aui-grid-text">Navbar导航</view>
						</view>
						<view class="aui-grid" col="4">
							<view class="aui-grid-icon"><text class="iconfont iconnumberbox" style="font-size: 25px; color: #db639b;"></text></view>
							<view class="aui-grid-text">Number输入框</view>
						</view>
						<view class="aui-grid" col="4">
							<view class="aui-grid-icon"><text class="iconfont iconnotice" style="font-size: 25px; color: #fe6503;"></text></view>
							<view class="aui-grid-text">Notice通告栏</view>
						</view>
						<view class="aui-grid" col="4">
							<view class="aui-grid-icon"><text class="iconfont iconsearch" style="font-size: 22px; color: #197DE0;"></text></view>
							<view class="aui-grid-text">Searchbar搜索</view>
						</view>
						<view class="aui-grid" col="4">
							<view class="aui-grid-icon"><text class="iconfont iconxing" style="font-size: 22px; color: #fec002;"></text></view>
							<view class="aui-grid-text">Fav收藏按钮</view>
						</view>
						<view class="aui-grid" col="4">
							<view class="aui-grid-icon"><text class="iconfont iconclock" style="color: #EE0000;"></text></view>
							<view class="aui-grid-text">Countdown倒计时</view>
						</view>
						<view class="aui-grid" col="4">
							<view class="aui-grid-icon"><text class="iconfont iconheadlines" style="color: #add51d;"></text></view>
							<view class="aui-grid-text">Card卡片</view>
						</view>				
					</view>
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
	.content-top{width: 100%; line-height: 25px; padding: 20px 15px; box-sizing: border-box; font-size: 14px; color: #aaa;}
</style>
