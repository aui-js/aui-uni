<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="Color-颜色" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="content-top">
				Color-颜色提供多种常用色彩，可点击页面对应色块复制色值。
			</view>
			<view class="aui-card" v-for="(list, key) in lists" :key="key">
				<view class="aui-card-title"><text class="aui-card-title-line"></text>{{list.title}}</view>
				<view class="aui-card-main">
					<view class="list" v-for="(item, index) in list.items" :key="index" :style="{background: item.bg}" @click.stop="copyColor(item.bg)">
						<text :style="{color: item.color ? item.color : '#fff'}">{{item.name}}</text>
						<text :style="{color: item.color ? item.color : '#fff'}">{{item.bg}}</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import {aui} from '@/common/aui/js/aui.js';
	import auiHeader from '@/components/aui-header/aui-header.vue';
	import {colorData} from '@/pages/ui/color/color.js';
	export default {
		components: {
			auiHeader
		},
		data() {
			return {
				contentHeight: null,
				lists: [],
			}
		},
		mounted(){
			this.getColorData();
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
			getColorData(){
				var _this = this;
				_this.lists = colorData;
			},
			copyColor(color){
				aui.copy(color);
				uni.showToast({
				    title: '内容复制成功',
				    duration: 2000
				});
			},
		}
	}
</script>

<style>
	.content-top{width: 100%; background: #f4f4f4; line-height: 25px; padding: 20px 15px; box-sizing: border-box; font-size: 14px; color: #aaa;}
	.list{width: -webkit-calc((100% - 40px) / 4); width: calc((100% - 40px) / 4); text-align: center; padding: 10px; box-sizing: border-box; display: inline-block; vertical-align: top; margin: 0px 5px; border-radius: 5px;}
	.list-title{width: 100%; height: 40px; line-height: 40px; font-size: 15px; padding-left: 12px; box-sizing: border-box; color: #333; position: relative;}
	.list-title::before{content: ''; width: 3px; height: 14px; background: #03A9F4; border-radius: 5px; position: absolute; top: 13px; left: 0;}
	.list text:first-child{font-size: 14px; color: #FFF; display: block;}
	.list text:last-child{font-size: 12px; color: #FFF;}
</style>
