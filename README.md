# aui-uni
aui移动端UI组件库uni-app版
## 简介

> aui 是一套基于原生javascript开发的移动端UI组件库，包含常用js方法、字符校验、dialog提示弹窗、数字键盘、侧滑菜单、时间选择器、多级联动、聊天UI、项目常用模板......

## 特点

> 1、标准化，产品化</br>
> 2、更多复用，更快效率</br>
> 3、多人协作，更加统一</br>
> 4、维护方便</br>
> 5、易于使用</br>
> 6、减少UI设计时间

## 组件

#### aui-loading

参数  |  类型  |  描述  | 默认值 | 必选
---- | ----- | ------ | ----- | ----
type  | number | 1: 常用风格;</br> 2: 点击按钮后在按钮内显示加载动画;</br> 3: 四个方块旋转;</br> 4: 圆点放大缩小动画(全屏首次加载过度动画); </br>5: 圆点背景过度动画-微信小程序效果(全屏首次加载过度动画) | 1 | 否
msg  | string | 提示内容 | '' | 否
mask  | boolean | 是否显示遮罩蒙版 | true | 否
direction  | string | 横向("row")或纵向("col")控制 | 'col' | 否
theme  | number | type=3时，控制全屏或小窗展示（1：小窗; 2：全屏） | 1 | 否
style  | object | {</br>    bg: '背景',</br>  color: '文字颜色', </br>    maskBg: '遮罩层颜色', </br>  zIndex: '层级'</br>} | '' | 否

`插件引入：`
```html
<aui-loading 
  :show="auiLoading.show" 
  :type="auiLoading.type" 
  :direction="auiLoading.row" 
  :msg="auiLoading.msg" 
  :mask="auiLoading.mask"
></aui-loading>
```
```javascript
import auiLoading from '@/components/aui-loading/aui-loading.vue';
export default {
  components: {
    auiLoading
  },
  data() {
    return {
      auiLoading: {
        show: false,
        type: 4,
        direction: 'col',
        msg: '加载中',
        mask: false,

      }
    }
  },
  onShow() {
    var _this = this;
    this.auiLoading.show = true;
    setTimeout(function(){
     	 _this.auiLoading.show = false;
    },300)
  },
  onLoad() {

  },
  methods: {
   
  }
}
```

