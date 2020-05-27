<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="dialog模态弹窗" :left="{use: true, click: closeWin}"></aui-header>
		<!-- #endif -->
		<view class="aui-content">
			<view class="aui-list-title">1、大按钮风格</view>
			<view class="aui-btn aui-btn-blue dialog-0">alert单按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-1">confirm双按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-2">delete删除提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-3">prompt输入弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-4">自定义带图标提示弹窗</view>
			<view class="aui-list-title">2、小按钮风格</view>
			<view class="aui-btn aui-btn-blue dialog-5">alert单按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-6">confirm双按钮提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-7">delete删除提醒弹窗</view>
			<view class="aui-btn aui-btn-blue dialog-8">prompt输入弹窗</view>
			<view class="aui-list-title">3、两个以上按钮</view>
			<view class="aui-btn aui-btn-blue dialog-9">多按钮弹窗</view>
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
			}
		},
		methods: {
			openWin(url, opts){
				aui.openWin(url, opts)
			},
			closeWin(){
				aui.closeWin()
			},
		}
	}
</script>

<style>
	
</style>
