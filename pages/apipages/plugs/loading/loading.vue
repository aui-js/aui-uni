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
			<view class="aui-btn aui-btn-blue" @click.stop="showloadbutton($event)" data-type="2">
				按钮加载动画
				<aui-loading
					ref="auiLoadingButton" 
					:type="auiLoading.type"
					:msg="auiLoading.msg"
					:styles="{'color': '#FFFFFF', 'background': '#197DE0', 'borderRadius': '5px'}"
				></aui-loading>
			</view>
			<view class="aui-list-title">3、四方块旋转动画</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="3">全屏小窗加载动画（默认配置dark风格）</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="3" data-style="white" data-mask="true">全屏小窗加载动画（light风格）</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="3" data-theme="2">全屏大窗加载动画</view>
			<view class="aui-list-title">4、三平行四边形放大缩小(全屏首次加载过度动画)</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="4">全屏加载动画</view>
			<view class="aui-list-title">5、三圆点背景过度(全屏首次加载过度动画)</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="5">全屏加载动画</view>
		</view>
		<aui-loading
			ref="auiLoading"
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
			headerHeight(e){
				//console.log(e);
				const { windowWidth, windowHeight } = uni.getSystemInfoSync();
				// #ifdef APP-PLUS
					this.contentHeight = windowHeight - e + 'px';				
				// #endif
			},
			// 显示loading加载弹窗
			showload(e){
				var _this = this;
				_this.auiLoading.type = Number(e.currentTarget.dataset.type);
				aui.isDefine(e.currentTarget.dataset.direction) ? _this.auiLoading.direction = e.currentTarget.dataset.direction : _this.auiLoading.direction = 'col';
				e.currentTarget.dataset.style == "white" ? _this.auiLoading.styles = {background: "#FFF", color: "#909090"} : _this.auiLoading.styles = {};
				aui.isDefine(e.currentTarget.dataset.mask) ? _this.auiLoading.mask = true : _this.auiLoading.mask = false;
				aui.isDefine(e.currentTarget.dataset.theme) ? _this.auiLoading.theme = Number(e.currentTarget.dataset.theme) : _this.auiLoading.theme = 1;
				_this.$refs.auiLoading.show(); //显示loading				
				var Timer = setTimeout(function(){
					clearTimeout(Timer)
					_this.$refs.auiLoading.hide(); //隐藏loading
				},2000)
			},
			// 按钮内显示loading加载动画
			showloadbutton(e){
				var _this = this;
				_this.auiLoading.type = Number(e.currentTarget.dataset.type);
				_this.$refs.auiLoadingButton.show(); //显示loading				
				var Timer = setTimeout(function(){
					clearTimeout(Timer)
					_this.$refs.auiLoadingButton.hide(); //隐藏loading
				},2000)
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
