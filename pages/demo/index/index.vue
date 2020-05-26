<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="实例" :right="{use: true, click: openPopMenu}"></aui-header>
		<!-- #endif -->
		<view class="aui-content">
			<view class="aui-lists">
				
			</view>
		</view>
		<aui-footer currentIndex="1" @tabBarTap="tabBarTap"></aui-footer>
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
	import auiFooter from '@/components/aui-footer/aui-footer.vue';
	import auiLoading from '@/components/aui-loading/aui-loading.vue';
	export default {
		components: {
			auiLoading,
			auiHeader,
			auiFooter
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
			},
			tabBarTap(index){
				var _this = this;
				console.log(index);
				switch (Number(index)){
					case 0:
						_this.openWin('../../API/index/index');
						break;
					case 1:
						_this.openWin('demo/index/index');
						break;
					default:
						break;
				}
			},
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
		height: calc(100vh - 55px);
		/* #ifndef MP */
		height: calc(100vh - 50px - 55px);
		/* #endif */
	}
	.aui-list-left img{width: 18px; height: 18px; margin: -0 10px 0 0; display: inline-block; vertical-align: middle; position: relative; top: -1px;}
</style>
