<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="loading加载动画" :left="{use: true, click: closeWin}"></aui-header>
		<!-- #endif -->
		<view class="aui-content">
			<view class="aui-list-title">1、常用loading加载弹窗</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="1">全屏默认配置加载动画</view>
			<view class="aui-list-title">2、按钮内显示loading加载动画</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="2">
				按钮加载动画
				<aui-loading
					:show="auiLoading.show" 
					:type="auiLoading.type" 
					:direction="auiLoading.row" 
					:msg="auiLoading.msg" 
					:mask="auiLoading.mask"
					:styles="{'color': '#FFFFFF', 'background': '#197DE0', 'borderRadius': '5px'}"
				></aui-loading>
			</view>
			<view class="aui-list-title">3、特殊风格loading加载弹窗 -> 四方块旋转</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="3">全屏小窗加载动画（默认配置dark风格）</view>
			<view class="aui-list-title">4、三圆点放大缩小动画(全屏首次加载过度动画)</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="4">全屏加载动画</view>
			<view class="aui-list-title">5、三圆点背景过度动画(全屏首次加载过度动画)</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showload($event)" data-type="5">全屏加载动画</view>
		</view>
		<aui-loading
			v-if="auiLoading.type!=2"
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
				_this.auiLoading.show = true;
				setTimeout(function(){
					_this.auiLoading.show = false;
				},3000)
			},
		}
	}
</script>

<style>
	
</style>
