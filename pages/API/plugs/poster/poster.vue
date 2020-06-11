<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="poster广告弹窗" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<button class="aui-btn aui-btn-blue" @click.top="showPoster($event)">显示弹窗</button>			
		</view>
		<aui-toast
			ref="toast"
			:msg="auiToast.msg"
			:duration="auiToast.duration"
		></aui-toast>
		<aui-poster
			ref="poster"
			:mask="auiPoster.mask"
			:maskTapClose="auiPoster.maskTapClose"
			:image="auiPoster.image"
			@callback="auiPosterCallback"
		></aui-poster>
		<!-- 简单调用poster -->
		<!-- <aui-poster
			ref="poster"
			:image="auiPoster.image"
			@callback="auiPosterCallback"
		></aui-poster> -->
	</view>
</template>

<script>
	import {aui} from '@/common/aui/js/aui.js';
	import auiHeader from '@/components/aui-header/aui-header.vue';
	import auiToast from '@/components/aui-toast/aui-toast.vue';
	import auiPoster from '@/components/aui-poster/aui-poster.vue';
	export default {
		components: {
			auiHeader,
			auiToast,
			auiPoster
		},
		data() {
			return {
				contentHeight: null,
				auiToast: {
					msg: '网络连接错误，请稍后再试',
					duration: 2000,
				},
				auiPoster: {					
					mask: true,
					maskTapClose: false,
					image: 'https://xbjz1.oss-cn-beijing.aliyuncs.com/upload/default/share.png'
				}
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
			showPoster(e){
				var _this = this;				
				_this.$refs.poster.show();
			},
			auiPosterCallback(e){
				var _this = this;
				console.log(e);
				_this.auiToast.msg = '您关闭了广告弹窗';
				_this.$refs.toast.show();	
			}
		}
	}
</script>

<style>
	.aui-content{padding: 15px 0 0 0;}
</style>
