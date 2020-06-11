<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="位置" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="aui-lists">
				<view class="aui-list" onclick="aui.openWin('actionmenu.html')">
					<view class="aui-list-left">amap高德地图</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" @click.stop="openWin('actionsheet/actionsheet')">
					<view class="aui-list-left">bmap百度地图</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>			
			</view>
			<view class="map" id="map"></view>
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
	
</style>
