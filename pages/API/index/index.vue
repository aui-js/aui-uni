<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="aui-uni" :right="{use: true, click: openPopMenu}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="aui-lists">
				<view class="aui-list" @click.stop="openWin('../plugs/login/login')">
					<view class="aui-list-left">
						<!-- #ifdef APP-PLUS || H5 -->
						<img src="static/index-0.png" alt="">
						<!-- #endif -->
						<!-- #ifdef MP -->
						<img src="@/static/index-0.png" alt="">
						<!-- #endif -->
						设备
					</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('html/events/event-index.html')">
					<view class="aui-list-left">
						<!-- #ifdef APP-PLUS || H5 -->
						<img src="static/index-1.png" alt="">
						<!-- #endif -->
						<!-- #ifdef MP -->
						<img src="@/static/index-1.png" alt="">
						<!-- #endif -->
						事件
					</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" @click.stop="openWin('../plugs/index/index')">
					<view class="aui-list-left">
						<!-- #ifdef APP-PLUS || H5 -->
						<img src="static/index-2.png" alt="">
						<!-- #endif -->
						<!-- #ifdef MP -->
						<img src="@/static/index-2.png" alt="">
						<!-- #endif -->
						组件
					</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('html/address/address-index.html')">
					<view class="aui-list-left">
						<!-- #ifdef APP-PLUS || H5 -->
						<img src="static/index-3.png" alt="">
						<!-- #endif -->
						<!-- #ifdef MP -->
						<img src="@/static/index-3.png" alt="">
						<!-- #endif -->
						位置
					</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('html/service/service-index.html')">
					<view class="aui-list-left">
						<!-- #ifdef APP-PLUS || H5 -->
						<img src="static/index-4.png" alt="">
						<!-- #endif -->
						<!-- #ifdef MP -->
						<img src="@/static/index-4.png" alt="">
						<!-- #endif -->
						客服
					</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
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
		height: calc(100vh - 50px - 44px);
		/* #endif */		
		/* #ifdef MP */
		height: 100vh;
		/* #endif */
		/* #ifdef APP-PLUS */
		height: calc(100vh - 50px - 26px);
		/* #endif */
	}
	.aui-list-left img{width: 18px; height: 18px; margin: -0 10px 0 0; display: inline-block; vertical-align: middle; position: relative; top: -1px;}
</style>
