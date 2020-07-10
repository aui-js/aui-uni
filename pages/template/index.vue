<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="模板" :right="{use: true, click: openPopMenu}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="content-top">
				<view>Template</view>
				<text>常用页面模板，动态交互效果模板</text>
			</view>
			<view class="aui-grids">
				<view class="aui-grid" col="4" onclick="aui.openWin('search/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconsearch" style="font-size: 22px; color: #007AFF;"></text></view>
					<view class="aui-grid-text">Search搜索</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('sidemenu/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconlist" style="font-size: 28px; color: #F44336;"></text></view>
					<view class="aui-grid-text">侧滑菜单</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('upload/uploadimg.html')">
					<view class="aui-grid-icon"><text class="iconfont icontupianshangchuan" style="font-size: 22px; color: #2CB0B2;"></text></view>
					<view class="aui-grid-text">图片上传</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('imgview/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconimage1" style="font-size: 25px; color: #F44336;"></text></view>
					<view class="aui-grid-text">图片预览</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('cropper/index.html')">
					<view class="aui-grid-icon"><text class="iconfont icontupiancaijian" style="font-size: 22px; color: #8BC34A;"></text></view>
					<view class="aui-grid-text">图片裁剪</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('rgbaster/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconzhutise" style="font-size: 25px; color: #03A9F4;"></text></view>
					<view class="aui-grid-text">图片主色</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('rating/rating-index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconselect_fill" style="font-size: 35px; color: #FFB74D;"></text></view>
					<view class="aui-grid-text">星级评价</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('picker/index.html')">
					<view class="aui-grid-icon"><text class="iconfont icondatepicker1" style="font-size: 22px; color: #FB6802;"></text></view>
					<view class="aui-grid-text">选择器</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('selectmenu/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconxialaliebiao" style="font-size: 25px; color: #fec002;"></text></view>
					<view class="aui-grid-text">下拉选择</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('tabbar/tabbar-index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconxuanxiangqia1" style="font-size: 22px; color: #EC2B45;"></text></view>
					<view class="aui-grid-text">选项卡</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('qrcode/qrcode-index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconerweima" style="font-size: 25px; color: #12986D;"></text></view>
					<view class="aui-grid-text">生成二维码</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('clipboard/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconcopy" style="font-size: 25px; color: #007AFF;"></text></view>
					<view class="aui-grid-text">复制剪贴板</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('parabola/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconxingzhuang" style="font-size: 25px; color: #f6a820;"></text></view>
					<view class="aui-grid-text">加入购物车</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('wave/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconweibiaoti-zhuanhuan-" style="font-size: 28px; color: #8BC34A;"></text></view>
					<view class="aui-grid-text">波浪特效</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('waterbubble/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconqiu" style="font-size: 25px; color: #FB6802;"></text></view>
					<view class="aui-grid-text">水球图</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('countdown/index.html')">
					<view class="aui-grid-icon"><text class="iconfont icondaojishi" style="font-size: 22px; color: #EC2B45;"></text></view>
					<view class="aui-grid-text">倒计时</view>
				</view>
				<view class="aui-grid" col="4" onclick="aui.openWin('facerecognition/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconrenlianshibie" style="font-size: 25px; color: #03A9F4;"></text></view>
					<view class="aui-grid-text">人脸识别</view>
				</view>
				<view class="aui-grid" col="4" style="display: none;" onclick="aui.openWin('redpacket/index.html')">
					<view class="aui-grid-icon"><text class="iconfont iconredpacket_fill" style="font-size: 28px; color: #FF5555;"></text></view>
					<view class="aui-grid-text">红包雨</view>
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
		height: calc(100vh - 50px);
		/* #endif */
	}
	.content-top{width: 100%; padding: 20px; box-sizing: border-box;}
	.content-top view{width: 100%; line-height: 40px; font-size: 18px; color: #333;}
	.content-top text{width: 100%; line-height: 20px; font-size: 13px; color: #888;}
</style>
