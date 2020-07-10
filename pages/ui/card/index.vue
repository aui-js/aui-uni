<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="Card卡片" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="content-top">
				Card卡片组件通常用来显示完整独立的一段信息，例如一篇文章的预览图、作者信息、时间等。卡片通常是更复杂信息的入口点。
			</view>
			<view class="aui-card">
				<view class="aui-card-title"><text class="aui-card-title-line"></text>基础卡片</view>
				<view class="aui-card-main">
					
					<!-- 卡片实例 -->
					<!-- 1、 -->
					<view class="aui-card" shandow radius>
						<view class="aui-card-main">
							<text>这是一个基础卡片示例，内容比较少，内容样式可自定义。</text>
						</view>
					</view>
					<!-- 2、 -->
					<view class="aui-card" shandow radius>
						<view class="aui-card-title">标题文字<view class="aui-card-title-right aui-text-gray">额外信息</view></view>
						<view class="aui-card-main">
							<text>这个一个基础卡片示例，内容比较多，内容样式可自定义，卡片识图通常用来显示完整独立的一段信息，比如一篇文章的预览图、作者信息、时间等。</text>
						</view>
					</view>
					<!-- 3、 -->
					<view class="aui-card" shandow radius>
						<view class="aui-card-title">标题文字<view class="aui-card-title-right aui-text-gray">额外信息</view></view>
						<view class="aui-card-main">
							<text>这个一个基础卡片示例，底部带提示信息，具体样式可自定义。</text>
						</view>
						<view class="aui-card-down row-before">
							<text class="aui-card-down-tip">Tips</text>
						</view>
					</view>
					<!-- 4、 -->
					<view class="aui-card" shandow radius>
						<view class="aui-card-title">
							标题文字
							<view class="aui-card-title-right aui-text-gray">额外信息<i class="iconfont aui-btn-right iconright1"></i></view>
						</view>
						<view class="aui-card-main">
							<text>这个一个基础卡片示例，内容比较多，内容样式可自定义，卡片识图通常用来显示完整独立的一段信息，比如一篇文章的预览图、作者信息、时间等。</text>
						</view>
						<view class="aui-card-down row-before" style="padding: 0;">
							<view class="aui-list" style="background: none;">
								<view class="aui-list-left"><img src="@/static/success-green.png" alt="">设备</view>
								<view class="aui-list-right" @click.stop="closeWin()"><text style="color: #aaa;">查看更多</text><i class="iconfont aui-btn-right iconright1"></i></view>
							</view>
						</view>
					</view>
					
					
				</view>
			</view>
			<view class="aui-card">
				<view class="aui-card-title"><text class="aui-card-title-line"></text>图文卡片</view>
				<view class="aui-card-main">
					
					<view class="aui-card aui-card-image" shandow radius>
						<view class="aui-card-main">
							<view class="img">
								<img src="@/static/logo.png" alt="">
								<view class="img-mask">aui框架</view>
							</view>
							<view class="desc">aui 是一套基于原生javascript开发的移动端UI组件库，包含常用js方法、字符校验、dialog提示弹窗、数字键盘、侧滑菜单、时间选择器、多级联动、聊天UI、项目常用模板…</view>
						</view>
						<view class="aui-card-down row-before">
							<view class="aui-btn"><i class="iconfont iconsend"></i>转发</view>
							<view class="aui-btn"><i class="iconfont iconmessage"></i>评论</view>
							<view class="aui-btn"><i class="iconfont iconpraise"></i>赞</view>
						</view>
					</view>
					
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
				contentHeight: null,
			}
		},
		mounted(){
		
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
			
		}
	}
</script>

<style>
	.content-top{width: 100%; line-height: 25px; padding: 20px 15px; box-sizing: border-box; font-size: 14px; color: #aaa;}
	.aui-card{margin-bottom: 10px;}
	.aui-card-main text{line-height: 25px; font-size: 13px; color: #333;}
</style>
