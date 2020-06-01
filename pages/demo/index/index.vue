<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="实例" :right="{use: true, click: openPopMenu}"></aui-header>
		<!-- #endif -->
		<view class="aui-content">
			<view class="aui-lists">
				<div class="aui-list" onclick="aui.openWin('sidemenu/index.html')">
						<div class="aui-list-left"><i class="iconfont iconother" style="font-size: 30px; left: -5px; color: #F44336;"></i>侧滑菜单</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('upload/uploadimg.html')">
						<div class="aui-list-left"><i class="iconfont icontupianshangchuan" style="font-size: 18px; color: #2CB0B2;"></i>图片上传</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('imgview/index.html')">
						<div class="aui-list-left"><i class="iconfont iconimage1" style="font-size: 20px; color: #F44336;"></i>图片预览</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('cropper/index.html')">
						<div class="aui-list-left"><i class="iconfont icontupiancaijian" style="font-size: 18px; color: #8BC34A;"></i>图片裁剪</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('rgbaster/index.html')">
						<div class="aui-list-left"><i class="iconfont iconzhutise" style="font-size: 20px; color: #2CB0B2;"></i>获取图片主题色</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('rating/rating-index.html')">
						<div class="aui-list-left"><i class="iconfont iconselect_fill" style="font-size: 28px; color: #FFB74D; left: -4px;"></i>星级评价</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('picker/index.html')">
						<div class="aui-list-left"><i class="iconfont icondatepicker1" style="font-size: 18px; color: #FB6802; top: 1px;"></i>选择器</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('selectmenu/index.html')">
						<div class="aui-list-left"><i class="iconfont iconxialaliebiao" style="font-size: 20px; color: #73B9EC;"></i>下拉选择</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('tabbar/tabbar-index.html')">
						<div class="aui-list-left"><i class="iconfont iconxuanxiangqia1" style="font-size: 18px; color: #EC2B45; top: 1px;"></i>选项卡</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('qrcode/qrcode-index.html')">
						<div class="aui-list-left"><i class="iconfont iconerweima" style="font-size: 20px; color: #12986D;"></i>生成二维码</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('clipboard/index.html')">
						<div class="aui-list-left"><i class="iconfont iconcopy" style="font-size: 20px; color: #007AFF;"></i>复制到剪贴板</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('parabola/index.html')">
						<div class="aui-list-left"><i class="iconfont iconxingzhuang" style="font-size: 24px; color: #f6a820;"></i>抛物线(加入购物车)</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('wave/index.html')">
						<div class="aui-list-left"><i class="iconfont iconweibiaoti-zhuanhuan-" style="font-size: 24px; color: #8BC34A;"></i>波浪特效</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('waterbubble/index.html')">
						<div class="aui-list-left"><i class="iconfont iconqiu" style="font-size: 20px; color: #FB6802;"></i>水球图</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('countdown/index.html')">
						<div class="aui-list-left"><i class="iconfont icondaojishi" style="font-size: 20px; color: #EC2B45; top: 1px;"></i>倒计时</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<div class="aui-list" onclick="aui.openWin('facerecognition/index.html')">
						<div class="aui-list-left"><i class="iconfont iconrenlianshibie" style="font-size: 24px; color: #197DE0;"></i>人脸识别</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div>
					<!-- <div class="aui-list" onclick="aui.openWin('redpacket/index.html')">
						<div class="aui-list-left"><i class="iconfont iconredpacket_fill" style="font-size: 24px; color: #FF5555;"></i>红包雨</div>
						<div class="aui-list-right"><i class="iconfont aui-btn-right iconright1"></i></div>
					</div> -->
				</div>
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
	.aui-list-left i{width: 30px; height: 100%; line-height: 53px; text-align: left; display: inline-block; vertical-align: top; position: relative;}
</style>
