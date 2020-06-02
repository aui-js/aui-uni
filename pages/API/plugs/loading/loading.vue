<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="loading加载动画" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="aui-list-title">1、常用loading加载动画</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="1">全屏默认配置加载动画</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="1" data-direction="row">全屏水平布局加载动画</view>
			<view class="aui-list-title">2、按钮内显示loading加载动画</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="2">
				按钮加载动画
				<aui-loading
					v-if="auiLoading.type==2"
					:show="auiLoading.show" 
					:type="auiLoading.type" 
					:direction="auiLoading.row" 
					:msg="auiLoading.msg" 
					:mask="auiLoading.mask"
					:styles="{'color': '#FFFFFF', 'background': '#197DE0', 'borderRadius': '5px'}"
				></aui-loading>
			</view>
			<view class="aui-list-title">3、四方块旋转动画</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="3">全屏小窗加载动画（默认配置dark风格）</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="3" data-mask="true" data-styles="{'background': '#FFF', 'color': '#909090'}">全屏小窗加载动画（light风格）</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="3" data-theme="2">全屏大窗加载动画</view>
			<view class="aui-list-title">4、三平行四边形放大缩小(全屏首次加载过度动画)</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="4">全屏加载动画</view>
			<view class="aui-list-title">5、三圆点背景过度(全屏首次加载过度动画)</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="5">全屏加载动画</view>
		</view>
		<aui-loading
			v-if="auiLoading.type!=2"
			:show="auiLoading.show" 
			:type="auiLoading.type" 
			:msg="auiLoading.msg" 
			:mask="auiLoading.mask"
			:direction="auiLoading.direction"
			:styles="auiLoading.styles"
			:theme="auiLoading.theme"
		></aui-loading>
		<!-- 简单调用 -->
		<!-- <aui-loading :show="auiLoading.show" msg="加载中"></aui-loading> -->
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
					msg: '加载中',
					mask: false,
					direction: 'col',
					styles: {},
					theme: 1
				},
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
			showload(e){
				var _this = this;
				_this.auiLoading.type = Number(e.currentTarget.dataset.type);
				_this.auiLoading.direction = aui.isDefine(e.currentTarget.dataset.direction) ? e.currentTarget.dataset.direction : 'col';
				_this.auiLoading.styles = eval('(' + e.currentTarget.dataset.styles + ')') ? eval('(' + e.currentTarget.dataset.styles + ')') : {};
				_this.auiLoading.mask = aui.isDefine(e.currentTarget.dataset.mask) ? true : false;
				_this.auiLoading.theme = aui.isDefine(e.currentTarget.dataset.theme) ? Number(e.currentTarget.dataset.theme) : 1;
				_this.auiLoading.show = true;
				setTimeout(function(){
					_this.auiLoading.show = false;
				},3000)
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
	.aui-content{
		/* #ifdef H5 */
		height: calc(100vh - 44px);
		/* #endif */		
		/* #ifdef MP */
		height: 100vh;
		/* #endif */
		/* #ifdef APP-PLUS */
		height: calc(100vh - 50px - 28px);
		/* #endif */
	}
</style>
