<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="aui-uni" :right="{use: true, click: openPopMenu}"></aui-header>
		<!-- #endif -->
		<view class="aui-content">
			<view class="aui-lists">
				<view class="aui-list" @click.stop="openWin('../plugs/login/login')">
					<view class="aui-list-left"><img src="@/static/index-0.png" alt="">设备</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('html/events/event-index.html')">
					<view class="aui-list-left"><img src="@/static/index-1.png" alt="">事件</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" @click.stop="openWin('../plugs/index/index')">
					<view class="aui-list-left"><img src="@/static/index-2.png" alt="">组件</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('html/address/address-index.html')">
					<view class="aui-list-left"><img src="@/static/index-3.png" alt="">位置</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('html/service/service-index.html')">
					<view class="aui-list-left"><img src="@/static/index-4.png" alt="">客服</view>
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
				title: 'Hello'
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
		height: calc(100vh - 50px);
		/* #ifndef MP */
		height: calc(100vh - 50px - 50px);
		/* #endif */
		/* #ifdef APP-PLUS */
		height: calc(100vh - 50px);
		/* #endif */
	}
	.aui-list-left img{width: 18px; height: 18px; margin: -0 10px 0 0; display: inline-block; vertical-align: middle; position: relative; top: -1px;}
</style>
