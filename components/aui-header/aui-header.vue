<template name="aui-header">
	<view class="aui-header">
		<view class="aui-header-left" v-if="left.use" @click.stop="left.click"><view class="iconfont iconreturn"></view></view>
		<view class="aui-header-title" style="left: 15px;">{{title}}</view>
		<view class="aui-header-right" v-if="right.use" @click.stop="right.click"><view class="iconfont iconother"></view></view>
	</view>
</template>

<script>
	export default {
		name: 'aui-heaader',
		props: {
			title: {
				type: String,
				default: 'aui-uni'
			},
			left: {
				type: Object,
				default () {
					return {
						use: false,
						icon: '',
						click: Function
					};
				}
			},
			right: {
				type: Object,
				default () {
					return {
						use: false,
						icon: '',
						click: Function
					};
				}
			}
		},
		data() {
			return {
				
			};
		},
		created(){
			//console.log(this.title);
		},
		onLoad() {
			//console.log(this.title);
		},
		methods: {
			closeWin(){
				aui.closeWin()
			},
		}
	}
</script>

<style>
	.aui-header{
		width: 100vw;
		height: 50px;
		background: linear-gradient(to right, #197DE0, #73B9EC);
		overflow: hidden;
		position: relative;
		left: 0;
		top: 0;
		z-index: 997;
	}
	.aui-header:before{
		content: '';
		width: 100px;
		height: 50px;	
		background: linear-gradient(to right, #FF5555, #FF7777);
		opacity: .9;
		transform: skewX(45deg);
		position: absolute;
		left: -25px;
		top: 0;
	}
	.aui-header-left{
		width: 44px;
		height: 50px;
		line-height: 50px;
		text-align: center;
		position: absolute;
		bottom: 0;
		left: 0;
		z-index: 996;
	}
	.aui-header-left .iconfont{
		font-size: 25px;
		color: #FFF;
	}
	.aui-header-title{
		height: 50px;
		line-height: 50px;
		color: #FFF;
		font-size: 18px;
		text-align: center;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
		position: absolute;
		left: 44px;
		right: 44px;
		bottom: 0;
	}
	.aui-header-right{
		width: 44px;
		height: 50px;
		line-height: 50px;
		text-align: center;
		position: absolute;
		bottom: 0;
		right: 0;
	}
	.aui-header-right .iconfont{
		font-size: 30px;
		padding: 1px 0 0 0;
		box-sizing: border-box;
		display: inline-block;
		color: #FFF;
		position: absolute;
		top: 50%;
		left: 50%;
		-ms-transform: translate(-50%, -50%);
		-webkit-transform: translate(-50%, -50%);
		transform: translate(-50%, -50%);
	}
</style>
