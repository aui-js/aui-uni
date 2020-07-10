<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="组件" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="content-top">
				<view>Basic</view>
				<text>基础组件、常用组件</text>
			</view>
			<view class="aui-grids">
				<view class="aui-grid" col="3" @click.stop="openWin('color/index')">
					<view class="aui-grid-icon"><text class="iconfont iconcolor" style="color: #EE0000;"></text></view>
					<view class="aui-grid-text">Color色彩</view>
				</view>
				<view class="aui-grid" col="3" @click.stop="aui.openWin('button/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconanniu" style="color: #eb077a;"></text></view>
					<view class="aui-grid-text">Button按钮</view>
				</view>
				<view class="aui-grid" col="3" @click.stop="aui.openWin('tag/index.html')">
					<view class="aui-grid-icon"><text class="iconfont icontag" style="font-size: 25px; color: #fe2f24;"></text></view>
					<view class="aui-grid-text">Tag标签</view>
				</view>
				<view class="aui-grid" col="3" @click.stop="aui.openWin('badge/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconbadge" style="font-size: 28px; color: #fec002;"></text></view>
					<view class="aui-grid-text">Badge数字角标</view>
				</view>
				<view class="aui-grid" col="3" @click.stop="aui.openWin('list/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconlist" style="font-size: 28px; color: #add51d;"></text></view>
					<view class="aui-grid-text">List列表</view>
				</view>
				<view class="aui-grid" col="3" @click.stop="aui.openWin('grid/index.html')">
					<view class="aui-grid-icon"><text class="iconfont icongrid" style="font-size: 22px; color: #fe6503;"></text></view>
					<view class="aui-grid-text">Grid九宫格</view>
				</view>
				<view class="aui-grid" col="3" @click.stop="aui.openWin('card/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconheadlines" style="color: #03A9F4;"></text></view>
					<view class="aui-grid-text">Card卡片</view>
				</view>
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont iconindexlist" style="color: #05c091;"></text></view>
					<view class="aui-grid-text">Index索引列表</view>
				</view>
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont iconnavbar" style="color: #fe2f24;"></text></view>
					<view class="aui-grid-text">Navbar导航</view>
				</view>
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont iconnumberbox" style="font-size: 25px; color: #db639b;"></text></view>
					<view class="aui-grid-text">Number输入框</view>
				</view>
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont iconnotice" style="font-size: 25px; color: #fe6503;"></text></view>
					<view class="aui-grid-text">Notice通告栏</view>
				</view>
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont iconsearch" style="font-size: 22px; color: #197DE0;"></text></view>
					<view class="aui-grid-text">Searchbar搜索</view>
				</view>
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont iconxing" style="font-size: 22px; color: #fec002;"></text></view>
					<view class="aui-grid-text">Fav收藏按钮</view>
				</view>
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont iconclock" style="color: #EE0000;"></text></view>
					<view class="aui-grid-text">Countdown倒计时</view>
				</view>					
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont iconzhedie" style="color: #05c091;"></text></view>
					<view class="aui-grid-text">Collapse折叠面板</view>
				</view>
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont icon17" style="font-size: 25px; color: #03A9F4;"></text></view>
					<view class="aui-grid-text">Progress进度条</view>
				</view>
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont iconprogress1" style="color: #fe6503;"></text></view>
					<view class="aui-grid-text">Steps步骤条</view>
				</view>
				<view class="aui-grid" col="3" style="display: none;">
					<view class="aui-grid-icon"><text class="iconfont icongoods" style="font-size: 25px; color: #fe2f24;"></text></view>
					<view class="aui-grid-text">Goods商品导航</view>
				</view>
			</view>
		</view>
		<aui-loading 
			:show="auiLoading.show" 
			:type="auiLoading.type" 
			:direction="auiLoading.row" 
			:msg="auiLoading.msg" 
			:mask="auiLoading.mask"
		></aui-loading>
	</view>
</template>

<script>
	import {aui} from '@/common/aui/js/aui.js';
	import auiHeader from '@/components/aui-header/aui-header.vue';
	import auiLoading from '@/components/aui-loading/aui-loading.vue';
	export default {
		components: {
			auiLoading,
			auiHeader
		},
		data() {
			return {
				auiLoading: {
					show: false,
					type: 4,
					direction: 'col',
					msg: '加载中',
					mask: false,
					
				},
				contentHeight: null
			}
		},
		onShow() {
			var _this = this;
			
			// this.auiLoading.show = true;
			// setTimeout(function(){
			// 	_this.auiLoading.show = false;
			// },300)
		},
		onLoad() {
			
		},
		methods: {
			openWin(url, opts){
				aui.openWin(url, opts)
			},
			openPopMenu(){
				alert('打开菜单')
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
	
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.aui-content{
		/* #ifdef H5 */
		height: calc(100vh - 50px - 50px);
		/* #endif */		
		/* #ifdef MP */
		height: 100vh;
		/* #endif */
		/* #ifdef APP-PLUS */
		height: calc(100vh - 50px - 26px);
		/* #endif */
	}
	.content-top{width: 100%; padding: 20px; box-sizing: border-box;}
	.content-top view{width: 100%; line-height: 40px; font-size: 18px; color: #333;}
	.content-top text{width: 100%; line-height: 20px; font-size: 13px; color: #888;}
</style>
