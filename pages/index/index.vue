<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<view class="showload-btn" @click.stop="showload()">显示loading加载</view>
		<aui-loading :show="auiLoading.show" direction="row" msg="加载中" :mask="true"></aui-loading>
	</view>
</template>

<script>
	import auiLoading from '@/components/aui-loading/aui-loading.vue';
	export default {
		components: {
			auiLoading
		},
		data() {
			return {
				auiLoading: {
					show: false,
					mask: false,
					
				},
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
			showload(){
				var _this = this;
				this.auiLoading.show = true;
				console.log(this.show)
				setTimeout(function(){
					_this.auiLoading.show = false;
				},1000)
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

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
