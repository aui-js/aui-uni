<template>
	<view class="content">
		<!-- #ifndef MP -->
		<aui-header title="picker多级联动弹窗" :left="{use: true, click: closeWin}" @headerHeight="headerHeight"></aui-header>
		<!-- #endif -->
		<view class="aui-content" :style="{height: contentHeight}">
			<view class="aui-btn aui-btn-blue" @click.stop="showPicker($event)" data-layer="1">picker一级联动</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showPicker($event)" data-layer="2">picker二级联动</view>
			<view class="aui-btn aui-btn-blue" @click.stop="showPicker($event)" data-layer="3">picker三级联动</view>	
			<view class="aui-btn aui-btn-blue" @click.stop="showPickerMax($event)">picker无限级联动</view>	
		</view>
		<aui-picker 
			ref="picker" 
			:title="auiPicker.title"
			:layer="auiPicker.layer"
			:data="auiPicker.data"
			@callback="pickerCallback"
		></aui-picker>
	</view>
</template>

<script>
	import {aui} from '@/common/aui/js/aui.js';
	import {cityData} from '@/common/city.data.js'; //城市数据
	import auiHeader from '@/components/aui-header/aui-header.vue';
	import auiPicker from '@/components/aui-picker/aui-picker.vue';
	export default {
		components: {
			auiHeader,
			auiPicker
		},
		data() {
			return {
				contentHeight: null,
				auiPicker: {
					title: 'picker多级联动',
					layer: null,
					data: []
				},
			}
		},
		created(){
			
		},
		mounted() {
			
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
			//显示picker多级联动弹窗
			showPicker(e){
				const _this = this;
				_this.auiPicker.layer = Number(e.currentTarget.dataset.layer) || null;
				_this.auiPicker.data = cityData;
				_this.$refs.picker.open().then(function(){
					console.log('picker打开');
				});
			},
			//显示picker多级联动弹窗
			showPickerMax(e){
				const _this = this;
				_this.auiPicker.layer = null;
				_this.auiPicker.data=[{
					id: "1001",
					name: "一级菜单1",
					children: [{
						id: "1002",
						name: "二级菜单1-1",
						children: [{
							id: "1003",
							name: "三级菜单1-1",
							children: [{
								id: "1004",
								name: "四级菜单1-1"
							}]
						}]
					}]
				},
				{
					id: "1005",
					name: "一级菜单2",
					children: [{
						id: "1006",
						name: "二级菜单2-1",
						children: [{
							id: "1007",
							name: "三级菜单2-1",
							children: [{
								id: "1008",
								name: "四级菜单2-1"
							}]
						}]
					}]
				}];
				_this.$refs.picker.open().then(function(){
					console.log('picker打开');
				});
			},
			//picker多级联动回调
			pickerCallback(e){
				const _this = this;
				console.log(e);
				const result = '';
				e.data.forEach(function(item, index){
					result += item.name + '   ';
				});
				alert(result);
			}
		}
	}
</script>

<style>
	.aui-content{padding: 15px 0 0 0;}
</style>
