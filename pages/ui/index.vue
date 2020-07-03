<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="组件" :right="{use: true, click: openPopMenu}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="aui-lists">
				
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
		height: calc(100vh - 50px - 44px);
		/* #endif */		
		/* #ifdef MP */
		height: 100vh;
		/* #endif */
		/* #ifdef APP-PLUS */
		height: calc(100vh - 50px);
		/* #endif */
	}
	.aui-list-left i{width: 30px; height: 100%; line-height: 53px; text-align: left; display: inline-block; vertical-align: top; position: relative;}
</style>
