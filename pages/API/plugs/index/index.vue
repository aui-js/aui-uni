<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="组件" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="aui-lists">
				<view class="aui-list" onclick="aui.openWin('actionmenu.html')">
					<view class="aui-list-left">actionMenu 底部菜单</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('actionsheet.html')">
					<view class="aui-list-left">actionSheet 操作表</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('chatbox.html')">
					<view class="aui-list-left">chatbox聊天页面底部UI插件</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('datepicker.html')">
					<view class="aui-list-left">datepicker时间选择器</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" @click.stop="openWin('../dialog/dialog')">
					<view class="aui-list-left">dialog 模态弹窗</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('keypad.html')">
					<view class="aui-list-left">keypad 数字键盘</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" @click.stop="openWin('../loading/loading')">
					<view class="aui-list-left">loading 加载动画</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('picker.html')">
					<view class="aui-list-left">picker 多级联动</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('popdownmenu.html')">
					<view class="aui-list-left">popdownmenu底部弹出窗口</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('popover.html')">
					<view class="aui-list-left">popover 弹出菜单</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('poptopmenu.html')">
					<view class="aui-list-left">poptopmenu顶部弹出窗口</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>	
				<view class="aui-list" onclick="aui.openWin('poster.html')">
					<view class="aui-list-left">poster 广告弹窗</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('selectmenu.html')">
					<view class="aui-list-left">selectmenu下拉列表选择框</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('sidemenu.html')">
					<view class="aui-list-left">sidemenu 侧滑菜单</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" @click.stop="openWin('../toast/toast')">
					<view class="aui-list-left">toast 消息提示</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
				<view class="aui-list" onclick="aui.openWin('wxshare.html')">
					<view class="aui-list-left">wxShare 微信分享提示弹窗</view>
					<view class="aui-list-right"><view class="iconfont aui-btn-right iconright1"></view></view>
				</view>
			</view>
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
