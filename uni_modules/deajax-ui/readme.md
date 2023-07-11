## 已实现组件：

### Button 按钮、Cell 单元格、Icon 图标、

### Layout 布局、Style 内置样式、Search 搜索、

### Stepper 步进器、Tag 标签、Tab 标签页、

### Card商品卡片、Divider 分割线、

### Empty 空状态、Grid 宫格、NavBar 导航栏、

### Loading 加载

​    

------

​           


>
> 写在前面：
>
> 因为公司业务需要使用到uni，所以一直在找合适的组件库，换了好多套最后发现都不太应心，几乎都是属于那种“作者给配置好能想到的所有属性，傻瓜式上手，你要的属性我都有”，“所有属性都写在view的标签上”的类型，就像taillwind，很难复用（taillwind可以封装css样式，但是组件再封装组件复用就很啰嗦）。想通过css来改写一些样式就很难，比如把cell组件改成一个商品展示组件，10条属性需要写9条!important来覆盖scoped带来的样式隔离，想再适配其他样式或者维护也是难上加难。
>
> 之前公司一直用的的vant的组件库，也用顺了手，但是无奈没有合适的uni版的vant，所以就突发奇想自己适配一套vant的组件库，刚开始是因为vant的cell组件在自家项目中应用范围很广，所以只想通过cell来解决一下目前的痛点，目前自家的项目用的都很好。
>
> 但是随着项目功能的增加，我发现我的痛点越来越多，所以我只能在不忙的时候扩展组件库的种类，不过扩展的组件完全取决于公司项目需求。且我是个设计人员，并非开发人员，很多功能我写不了或者写的有问题，仅仅只是能满足公司项目需求。
>
> 如果有我没测出来的bug也欢迎大家评论或去github提issue。
>
> 以上

​       

🗒 说明：

1. 手写的山寨vant组件，因为uni很多属性和vue不一样，所以只是模仿了vant组件的样式，属性和方法是自己硬适配的，并不是官方代码转换的。
2. 有些官方属性可能我没写上，要么是写不了，要么就是公司业务不需要。
3. 可能有bug，随时修复。
4. 有不属于vant的属性/样式，是因为自己公司业务需求自己额外加上的。
5. 部分属性使用了css变量，同vant，可以用变量来覆盖样式。
6. **样式和代码分离，没有scoped样式隔离**，样式优先级较低，可被轻易覆盖，用来自定义样式。
7. 默认开启了微信小程序的virtualHost属性（虚拟节点），这个带来的影响尚未确定。
7. 微信小程序和支付宝小程序都是测试过没问题的，h5样式和语法都有问题，项目主要针对支付宝和微信的，有时间了我会改改。如果使用H5的话，还是建议直接使用vant的vue版本。

​    

​     

------

### 🧑‍💻 以下是文档：

------

​    

**使用方法**

1、从插件市场下载后配置pages.json文件：

```json
"easycom": {
		"autoscan": true,
		"custom": {
			"^van-(.*)": "@/uni_modules/deajax-ui/components/van-$1/index.vue"
		}
}
```

2、在App.vue的style中引入 **基础样式** 和 **图标库**

```vue
<style lang="scss">
  //引入基础样式
  @import '@/uni_modules/deajax-ui/common/style.scss';
  //引入图标库
  @import '@/uni_modules/deajax-ui/remixicon/remixicon.scss';
</style>
```

​          

**自定义样式**

> 样式和代码分离，没有scoped样式隔离，样式优先级较低，可被轻易覆盖
>
> 比如想增加cell的padding：

vue:

```vue
// vue
<view class="big-cell-padding">
	<van-cell title="我想变的大一点" />
</view>

```

style.scss:

```scss
.big-cell-padding {
	.van-cell {
		padding: 16px 24px;
	}
}
//或者
.big-cell-padding {
  --van-cell-vertical-padding: 16px;
  --van-cell-horizontal-padding: 24px;
}
```

​    

## 基础样式变量

用以下变量覆盖uni.scss的原有内容或添加在uni.scss中，即可在全局使用此变量。

此变量为 Vant 组件的主题样式规范。

```scss
// Color Palette
$van-black: #000;
$van-white: #fff;
$van-gray-1: #f7f8fa;
$van-gray-2: #f2f3f5;
$van-gray-3: #ebedf0;
$van-gray-4: #dcdee0;
$van-gray-5: #c8c9cc;
$van-gray-6: #969799;
$van-gray-7: #646566;
$van-gray-8: #323233;
$van-red: #ee0a24;
$van-blue: #1989fa;
$van-orange: #ff976a;
$van-orange-dark: #ed6a0c;
$van-orange-light: #fffbe8;
$van-green: #07c160;

// Gradient Colors
$van-gradient-red: linear-gradient(to right, #ff6034, #ee0a24);
$van-gradient-orange: linear-gradient(to right, #ffd01e, #ff8917);

// Component Colors
$van-primary-color: $van-blue;
$van-success-color: $van-green;
$van-danger-color: $van-red;
$van-warning-color: $van-orange;
$van-text-color: $van-gray-8;
$van-text-color-2: $van-gray-6;
$van-text-color-3: $van-gray-5;
$van-text-link-color: #576b95;
$van-active-color: $van-gray-2;
$van-active-opacity: 0.6;
$van-disabled-opacity: 0.5;
$van-background-color: $van-gray-1;
$van-background-color-light: $van-white;

// Padding
$van-padding-base: 4px;
$van-padding-xs: 8px;
$van-padding-sm: 12px;
$van-padding-md: 16px;
$van-padding-lg: 24px;
$van-padding-xl: 32px;

// Font
$van-font-size-xs: 10px;
$van-font-size-sm: 12px;
$van-font-size-md: 14px;
$van-font-size-lg: 16px;
$van-font-weight-bold: 500;
$van-line-height-xs: 14px;
$van-line-height-sm: 18px;
$van-line-height-md: 20px;
$van-line-height-lg: 22px;
$van-base-font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', Helvetica, Segoe UI, Arial, Roboto, 'PingFang SC', 'miui', 'Hiragino Sans GB', 'Microsoft Yahei', sans-serif;
$van-price-integer-font-family: Avenir-Heavy, PingFang SC, Helvetica Neue, Arial, sans-serif;

// Animation
$van-animation-duration-base: 0.3s;
$van-animation-duration-fast: 0.2s;
$van-animation-timing-function-enter: ease-out;
$van-animation-timing-function-leave: ease-in;

// Border
$van-border-color: $van-gray-3;
$van-border-width-base: 1px;
$van-border-radius-sm: 2px;
$van-border-radius-md: 4px;
$van-border-radius-lg: 8px;
$van-border-radius-max: 999px;
```

​    

​        

## **内置样式**

> Vant 中默认包含了一些常用样式，可以直接通过 className 的方式使用



##### 引入

在 app.vue 中引入内置样式。

```js
@import '@/uni_modules/deajax-ui/common/style.scss';
```

##### 文字省略

```vue
<view class="van-ellipsis">
  这是一段宽度限制 250px 的文字，后面的内容会省略。
</view>

<!-- 最多显示两行 -->
<view class="van-multi-ellipsis--l2">
  这是一段最多显示两行的文字，后面的内容会省略。
</view>

<!-- 最多显示三行 -->
<view class="van-multi-ellipsis--l3">
  这是一段最多显示三行的文字，后面的内容会省略。
</view>
```

##### 1px 边框

```vue
<!-- 上边框 -->
<view class="van-hairline--top"></view>

<!-- 下边框 -->
<view class="van-hairline--bottom"></view>

<!-- 左边框 -->
<view class="van-hairline--left"></view>

<!-- 右边框 -->
<view class="van-hairline--right"></view>

<!-- 上下边框 -->
<view class="van-hairline--top-bottom"></view>

<!-- 全边框 -->
<view class="van-hairline--surround"></view>
```

##### 全局字体

推荐在 App.vue 的 style 中设置以下全局字体，以保证在不同设备上提供最佳的视觉体验。

```css
page {
  font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', Helvetica,
    Segoe UI, Arial, Roboto, 'PingFang SC', 'miui', 'Hiragino Sans GB', 'Microsoft Yahei',
    sans-serif;
}
```

​    

## Cell Group 单元格组

示例：

```vue
<template>
	<van-cell-group title="组标题">
    <van-cell title="单元格" value="内容"></van-cell>
    <van-cell title="单元格" value="内容" label="描述信息"></van-cell>
  </van-cell-group>
</template>
```

#### Props

| 参数   | 说明                   | 类型    | 默认值 |
| ------ | ---------------------- | ------- | ------ |
| title  | 分组标题               | String  | -      |
| inset  | 是否展示为圆角卡片风格 | Boolean | false  |
| border | 是否显示外边框         | Boolean | true   |

#### Slot
| 名称  | 说明                                              |
| ----- | ------------------------------------------------- |
| title | 自定义title显示内容,，如果设置了title属性则不生效 |

​    

​    

## Cell 单元格

> 图标使用Remix icon，可以直接在van-cell中使用，如：`<van-cell icon="ri-add-line" />`
>

示例：

```vue
<template>
	<van-cell title="单元格" label="描述信息" value="内容"></van-cell>
</template>
```

#### Props

| 参数             | 说明                                                        | 类型             | 默认值     |
| ---------------- | ----------------------------------------------------------- | ---------------- | ---------- |
| icon             | 左侧图标名称                                                | String           | -          |
| title            | 左侧标题                                                    | [String, Number] | -          |
| title-width      | 标题宽度，须包含单位                                        | String           | -          |
| value            | 右侧内容                                                    | [String, Number] | -          |
| label            | 标题下方的描述信息                                          | [String, Number] | -          |
| size             | 单元格大小，可选值为 `large`                                | String           | -          |
| border           | 是否显示下边框                                              | Boolean          | true       |
| center           | 是否使内容垂直居中                                          | Boolean          | false      |
| url              | 点击后跳转的链接地址                                        | String           | -          |
| clickable        | 是否开启点击反馈                                            | Boolean          | false      |
| is-link          | 是否展示右侧箭头并开启点击反馈                              | Boolean          | false      |
| link-type v0.1.1 | 链接跳转类型，可选值为 `redirectTo` `switchTab ` `reLaunch` | String           | navigateTo |

#### Slot
| 名称       | 说明                                                       |
| ---------- | ---------------------------------------------------------- |
| -          | 自定义value显示内容，如果设置了value属性则不生效           |
| title      | 自定义title显示内容，如果设置了title属性则不生效           |
| label      | 自定义label显示内容                                        |
| icon       | 自定义icon显示内容，如果设置了icon属性则不生效             |
| right-icon | 自定义右侧按钮，默认是arrow，如果设置了is-link属性则不生效 |
| extra      | 自定义右侧额外内容                                         |

​    

​    

## Card 商品卡片

> 商品卡片并未完全按照vant的样式和属性进行编写，只是为了方便实现业务。

示例：

```vue
<template>
	<van-card
				title="商品标题"
				desc="描述信息"
				price="2.00"
				num="2"
				thumb="https://via.placeholder.com/150"
				tag="标签"
				clickable
				@click="onClick"
			>
				<view slot="extra">extra</view>
	</van-card>
</template>

<script>
export default {
	methods: {
		onClick() {
			console.log('click card');
		}
	}
};
</script>
```

#### Props

| 参数       | 说明                              | 类型           | 默认值                              |
| ------------ | ----------------------------------- | ---------------- | ------------------------------------- |
| layout     | 布局，可选'vertical'              | String         | -                                   |
| title      | 标题                              | String         | -                                   |
| desc       | 描述                              | String         |                                       |
| num        | 商品数量                          | [String, Number] | 1                                   |
| thumb      | 左侧图片 URL                      | String         | -                                   |
| thumb-mode | 图片模式，同[uni image](https://uniapp.dcloud.io/component/image.html)组件的[mode](https://uniapp.dcloud.io/component/image.html)属性 | String         | 'aspectFill'                        |
| thumb-size | 左侧图片尺寸，单位尺寸px          | String         | css定义横向默认80，竖向100%且为正方形 |
| tag        | 图片角标                          | String         | -                                   |
| tag-style  | 图片角标样式                      | Object         | -                                   |
| price      | 商品价格                          | [String, Number] | 0.00                                |
| origin-price | 商品划线原价                      | [String, Number] | 0.00                                |
| unit `v0.3.16` | 商品单位 | String | 斤 |
| clickable  | 是否开启点击反馈                  | Boolean        | true                               |

####  Slot

| 名称         | 说明                   |
| ------------ | ---------------------- |
| tag          | 自定义图片角标         |
| thumb        | 自定义图片             |
| top          | 自定义上方区域         |
| title        | 自定义标题             |
| desc         | 自定义描述             |
| tags         | 自定义描述下方标签区域 |
| extra        | 自定义右侧额外内容     |
| bottom       | 自定义下方区域         |
| price        | 自定义价格             |
| origin-price | 自定义商品原价         |
| num          | 自定义数量             |

​    

​    

## Tab 标签页

> 这个组件太™难写了，好多属性实现不了，这个uni的方法都不一样啊，算了先凑合用吧。

⚠️‼️注意：tab必须声明 **name**，v-model默认为String类型的‘1’，所以如果你的name不是1234，那**v-model**也必填！

示例：

```vue
<template>
  <van-tabs v-model="value">
    <van-tab title="标签1" name="1">内容1</van-tab>
    <van-tab title="标签2" name="2">内容2</van-tab>
    <van-tab title="标签3" name="3">内容3</van-tab>
    <van-tab title="标签4" name="4">内容4</van-tab>
  </van-tabs>
</template>

<script>
export default {
	data() {
		return {
			value: '1',
		};
	}
};
</script>
```

#### Tabs Props

| 参数                 | 说明                                                         | 类型             | 默认值 |
| -------------------- | ------------------------------------------------------------ | ---------------- | ------ |
| v-model              | 当前选中标签的标识符                                         | [String, Number] | ‘1’    |
| type                 | 样式风格，可选值为card                                       | String           | line   |
| color                | 标签主题色                                                   | String           | -      |
| duration             | 动画时间，单位秒                                             | Number           | 0.3    |
| line-width           | 底部条宽度，默认单位px                                       | [String, Number] | 40     |
| line-height          | 底部条高度，默认单位px                                       | [String, Number] | 3      |
| animated             | 是否开启切换标签内容时的转场动画                             | Boolean          | false  |
| border               | 是否展示外边框，仅在 line 风格下生效                         | Boolean          | false  |
| ellipsis             | 是否省略过长的标题文字                                       | Boolean          | true   |
| sticky               | 是否使用粘性定位布局                                         | Boolean          | false  |
| swipeable            | 是否开启手势滑动切换                                         | 暂不支持         |        |
| lazy-render          | 是否开启标签页内容延迟渲染                                   | 暂不支持         |        |
| offset-top           | 粘性定位布局下与顶部的最小距离，单位px                       | Number           | -      |
| swipe-threshold      | 滚动阈值，标签数量超过阈值且总宽度超过标<br />签栏宽度时开始横向滚动 | Number           | 5      |
| title-active-color   | 标题选中态颜色                                               | String           | -      |
| title-inactive-color | 标题默认态颜色                                               | String           | -      |
| z-index              | z-index 层级                                                 | Number           | 10     |

#### Tab Props

| 参数            | 说明                       | 类型             | 默认值 |
| --------------- | -------------------------- | ---------------- | ------ |
| name (**必填**) | 标签名称，作为匹配的标识符 | [String, Number] | '1'    |
| title           | 标题                       | String           | -      |
| disabled        | 是否禁用标签               | 暂不支持         |        |
| dot             | 是否显示小红点             | Boolean          | false  |
| info            | 图标右上角提示信息         | [String, Number] | -      |
| title-style     | 自定义标题样式             | String           | -      |

#### Tabs Slot

| 名称      | 说明         |
| --------- | ------------ |
| nav-left  | 标题左侧内容 |
| nav-right | 标题右侧内容 |

#### Tab Slot

| 名称 | 说明       |
| ---- | ---------- |
| -    | 标签页内容 |

#### Tabs Event

| 名称   | 说明           | 参数                          |
| ------ | -------------- | ----------------------------- |
| @click | 点击标签时触发 | name：标签标识符，title：标题 |

​    

​    

## Icon 图标

> 图标使用了remixicon图标库，图标库拥有2271个图标，可以满足绝大部分场景，且分线、面两种类型，是我们目前项目一直在用的图标库，如果有其他图标库需求，可以在安装完图标库后，直接用图标名+前缀的方式来引用，比如用iconfont：name="iconfont iconfont-name"

remixicon图标库地址：https://remixicon.cn/ 

remixicon图标库git：https://github.com/Remix-Design/remixicon   

示例：

```vue
<template>
	<van-icon name="ri-vuejs-line"></van-icon>
</template>
```

#### Props

| 参数  | 说明                          | 类型   | 默认值 |
| ----- | ----------------------------- | ------ | ------ |
| name  | 图标名称                      | String | -      |
| color | 图标颜色                      | String | -      |
| size  | 图标大小，如 20，默认单位为px | String | -      |

#### Events

| 事件名 | 说明           |
| ------ | -------------- |
| @click | 点击图标时触发 |

​    

​    

## Button 按钮

>   ~~因为loading组件还没有做，所以写了一个简易版的button loading，和官方的loading效果有区别~~
>
>   0.3.16 已更换为van-loading组件。

示例：

```vue
<template>
	<van-button type="primary">主要按钮</van-button>
</template>
```

#### Props

| 参数               | 说明                                                         | 类型    | 默认值       |
| :----------------- | :----------------------------------------------------------- | :------ | :----------- |
| id                 | 标识符                                                       | string  | -            |
| type               | 按钮类型，可选值为 `primary` ` info` `warning` `danger`      | string  | default      |
| size               | 按钮尺寸，可选值为 `normal` `large` `small` `mini`           | string  | normal       |
| color              | 按钮颜色，支持传入linear-gradient渐变色                      | string  | -            |
| icon               | 左侧图标名称或图片链接，可选值见 [Icon 组件]                 | string  | -            |
| plain              | 是否为朴素按钮                                               | boolean | false        |
| block              | 是否为块级元素                                               | boolean | false        |
| round              | 是否为圆形按钮                                               | boolean | false        |
| square             | 是否为方形按钮                                               | boolean | false        |
| disabled           | 是否禁用按钮                                                 | boolean | false        |
| hairline           | 是否使用 0.5px 边框                                          | boolean | false        |
| loading            | 是否显示为加载状态                                           | boolean | false        |
| loading-text       | 加载状态提示文字                                             | string  | -            |
| loading-type       | 加载状态图标类型，可选值为 spinner                           | string  | circular     |
| loading-size       | 加载图标大小                                                 | string  | 20           |
| custom-style       | 自定义样式                                                   | string  | -            |
| open-type          | 微信开放能力，具体支持可参考 微信官方文档                    | string  | -            |
| app-parameter      | 打开 APP 时，向 APP 传递的参数                               | string  | -            |
| lang               | 指定返回用户信息的语言，zh_CN 简体中文， zh_TW 繁体中文，en 英文 | string  | en           |
| session-from       | 会话来源                                                     | string  | -            |
| business-id        | 客服消息子商户 id                                            | number  | -            |
| send-message-title | 会话内消息卡片标题                                           | string  | 当前标题     |
| send-message-path  | 会话内消息卡片点击跳转小程序路径                             | string  | 当前分享路径 |
| send-message-img   | sendMessageImg                                               | string  | 截图         |
| show-message-card  | 显示会话内消息卡片                                           | string  | false        |
| dataset            | 按钮 dataset，open-type 为 share 时，可在 onShareAppMessage 事件的 event.target.dataset.detail 中看到传入的值 | any     | -            |
| form-type          | 用于 form 组件，可选值为submit reset，点击分别会触发 form 组件的 submit/reset 事件 | string  | -            |

#### Events

| 事件名          | 说明                                                         | 参数 |
| :-------------- | :----------------------------------------------------------- | :--- |
| @click          | 点击按钮，且按钮状态不为加载或禁用时触发                     | -    |
| @getuserinfo    | 用户点击该按钮时，会返回获取到的用户信息， 从返回参数的 detail 中获取到的值同 wx.getUserInfo | -    |
| @contact        | 客服消息回调                                                 | -    |
| @getphonenumber | 获取用户手机号回调                                           | -    |
| @error          | 当使用开放能力时，发生错误的回调                             | -    |
| @opensetting    | 在打开授权设置页后回调                                       | -    |

​    

​    

## Search 搜索

示例：

```vue
<template>
	<van-search :value="value" placeholder="请输入搜索关键词" />
</template>

<script>
export default {
	data() {
		return {
			value: ''
		};
	}
};
</script>
```

### Props

| 参数                | 说明                                                         | 类型             | 默认值  |
| :------------------ | :----------------------------------------------------------- | :--------------- | :------ |
| name                | 在表单内提交时的标识符                                       | string           | -       |
| label               | 搜索框左侧文本                                               | string           | -       |
| shape               | 形状，可选值为 `round`                                       | string           | square  |
| value               | 当前输入的值                                                 | string \| number | -       |
| background          | 搜索框背景色                                                 | string           | #f2f2f2 |
| show-action         | 是否在搜索框右侧显示取消按钮                                 | boolean          | false   |
| action-text         | 取消按钮文字                                                 | string           | 取消    |
| focus               | 获取焦点                                                     | boolean          | false   |
| error               | 是否将输入内容标红                                           | boolean          | false   |
| disabled            | 是否禁用输入框                                               | boolean          | false   |
| readonly            | 是否只读                                                     | boolean          | false   |
| maxlength           | 最大输入长度，设置为 -1 的时候不限制最大长度                 | number           | -1      |
| use-action-slot     | 是否使用 `action slot`                                       | boolean          | false   |
| placeholder         | 输入框为空时占位符                                           | string           | -       |
| placeholder-style   | 指定占位符的样式                                             | string           | -       |
| input-align         | 输入框内容对齐方式，可选值为 `center` `right`                | string           | left    |
| use-left-icon-slot  | 是否使用输入框左侧图标 slot                                  | boolean          | false   |
| use-right-icon-slot | 是否使用输入框右侧图标 slot                                  | boolean          | false   |
| left-icon           | 输入框左侧图标名称或图片链接，可选值见 Icon 组件（如果设置了 use-left-icon-slot，则该属性无效） | string           | search  |
| right-icon          | 输入框右侧图标名称或图片链接，可选值见 Icon 组件（如果设置了 use-right-icon-slot，则该属性无效） | string           | -       |

### Events

| 事件名       | 说明               | 参数                     |
| :----------- | :----------------- | :----------------------- |
| @search      | 确定搜索时触发     | event.detail: 当前输入值 |
| @change      | 输入内容变化时触发 | event.detail: 当前输入值 |
| @cancel      | 取消搜索搜索时触发 | -                        |
| @focus       | 输入框聚焦时触发   | -                        |
| @blur        | 输入框失焦时触发   | -                        |
| @clear       | 点击清空控件时触发 | -                        |
| @click-input | 点击搜索区域时触发 | -                        |

### Slot

| 名称       | 说明                                                         |
| :--------- | :----------------------------------------------------------- |
| action     | 自定义搜索框右侧按钮，需要在`use-action-slot`为 true 时才会显示 |
| label      | 自定义搜索框左侧文本                                         |
| left-icon  | 自定义输入框左侧图标，需要在`use-left-icon-slot`为 true 时才会显示 |
| right-icon | 自定义输入框右侧图标，需要在`use-right-icon-slot`为 true 时才会显示 |

​    

​    

## Stepper 步进器

示例：

```vue
<template>
	<van-stepper :value="1" @change="onChange" />
</template>

<script>
export default {
	methods: {
		onChange(value) {}
	}
};
</script>
```



### Props

| 参数           | 说明                                                         | 类型               | 默认值  |
| :------------- | :----------------------------------------------------------- | :----------------- | :------ |
| name           | 在表单内提交时的标识符                                       | *string*           | -       |
| value          | 输入值                                                       | *string \| number* | 最小值  |
| min            | 最小值                                                       | *string \| number* | `1`     |
| max            | 最大值                                                       | *string \| number* | -       |
| step           | 步长                                                         | *string \| number* | `1`     |
| integer        | 是否只允许输入整数                                           | *boolean*          | `false` |
| disabled       | 是否禁用                                                     | *boolean*          | `false` |
| disable-input  | 是否禁用输入框                                               | *boolean*          | `false` |
| async-change   | 是否开启异步变更，开启后需要手动控制输入值                   | *boolean*          | `false` |
| input-width    | 输入框宽度，默认单位为 `px`                                  | *string \| number* | `32px`  |
| button-size    | 按钮大小，默认单位为 `px`，输入框高度会和按钮大小保持一致    | *string \| number* | `28px`  |
| show-plus      | 是否显示增加按钮                                             | *boolean*          | `true`  |
| show-minus     | 是否显示减少按钮                                             | *boolean*          | `true`  |
| decimal-length | 固定显示的小数位数                                           | *number*           | -       |
| theme          | 样式风格，可选值为 `round`                                   | *string*           | -       |
| disable-plus   | 是否禁用增加按钮                                             | *boolean*          | -       |
| disable-minus  | 是否禁用减少按钮                                             | *boolean*          | -       |
| always-embed   | 强制 input 处于同层状态，默认 focus 时 input 会切到非同层状态 (仅在 iOS 下生效) | *boolean*          | `false` |

### Events

| 事件名  | 说明                                               | 回调参数 |
| :------ | :------------------------------------------------- | :------- |
| @change | 输入框值改变时触发的事件，参数为输入框当前的 value | -        |
| @focus  | 输入框聚焦时触发的事件，参数为 event 对象          | -        |
| @blur   | 输入框失焦时触发的事件，参数为 event 对象          | -        |

### Slot

| 名称  | 说明     |
| :---- | :------- |
| plus  | 加号按钮 |
| minus | 减号按钮 |

​    

​    

## Layout 布局

示例：

```vue
<template>
	<van-row>
    <van-col span="8">span: 8</van-col>
    <van-col span="8">span: 8</van-col>
    <van-col span="8">span: 8</van-col>
  </van-row>

  <van-row>
    <van-col span="4">span: 4</van-col>
    <van-col span="10" offset="4">offset: 4, span: 10</van-col>
  </van-row>

	<van-row gutter="20" gap="20">
    <van-col span="8">span: 8</van-col>
    <van-col span="8">span: 8</van-col>
    <van-col span="8">span: 8</van-col>
    <van-col span="8">span: 8</van-col>
    <van-col span="8">span: 8</van-col>
    <van-col span="8">span: 8</van-col>
  </van-row>
</template>
```

### Row Props

| 参数   | 说明                            | 类型               | 默认值 |
| :----- | :------------------------------ | :----------------- | :----- |
| gutter | 列元素之间的间距（单位为 px）   | *string \| number* | -      |
| gap    | 列元素之间的行间距（单位为 px） | *string \| number*    | -      |
| justify | 水平排列方式，可选值为`start`、`end`、`center`、`around`、`between` | string | - |
| align | 垂直对齐方式，可选值为`top`、`center`、`bottom` | string | - |

### Col Props

| 参数   | 说明           | 类型               | 默认值 |
| :----- | :------------- | :----------------- | :----- |
| span   | 列元素宽度     | *string \| number* | -      |
| offset | 列元素偏移距离 | *string \| number* | -      |

​    

​    

## Tag 标签

示例：

```vue
<template>
	<van-tag type="primary">标签</van-tag>
  <van-tag type="success">标签</van-tag>
  <van-tag type="danger">标签</van-tag>
  <van-tag type="warning">标签</van-tag>
</template>
```

### Props

| 参数       | 说明                                                  | 类型      | 默认值  |
| :--------- | :---------------------------------------------------- | :-------- | :------ |
| type       | 类型，可选值为 `primary` `success` `danger` `warning` | *string*  | -       |
| size       | 大小, 可选值为 `large` `medium`                       | *string*  | -       |
| color      | 标签颜色                                              | *string*  | -       |
| plain      | 是否为空心样式                                        | *boolean* | `false` |
| round      | 是否为圆角样式                                        | *boolean* | `false` |
| mark       | 是否为标记样式                                        | *boolean* | `false` |
| text-color | 文本颜色，优先级高于 `color` 属性                     | *string*  | `white` |
| closeable  | 是否为可关闭标签                                      | *boolean* | `false` |

### Slot

| 名称 | 说明                |
| :--- | :------------------ |
| -    | 自定义 Tag 显示内容 |

### Events

| 事件名 | 说明           | 回调参数 |
| :----- | :------------- | :------- |
| @close | 关闭标签时触发 | -        |
| @click | 点击时触发     | -        |

​    

## Divider 分割线

示例：

```vue
<template>
	<van-divider />
</template>
```

### Props

| 参数             | 说明                              | 类型      | 默认值 |
| :--------------- | :-------------------------------- | :-------- | :----- |
| dashed           | 虚线                              | *boolean* | false  |
| hairline         | 细线                              | *boolean* | false  |
| content-position | 文本位置，`left` `center` `right` | *string*  | -      |
| custom-style     | 自定义样式                        | *string*  | -      |
| font-size        | 字体大小                          | string    | -      |
| text-color       | 文本颜色                          | string    | -      |
| border-color     | border 颜色                       | string    | -      |

### Slot

| 名称 | 说明           |
| :--- | :------------- |
| 默认 | 自定义文本内容 |

​    

​    

## Empty 空状态

示例：

```vue
<template>
	<van-empty description="描述文字" />
</template>
```

### Props

| 参数        | 说明                                                         | 类型     | 默认值    |
| :---------- | :----------------------------------------------------------- | :------- | :-------- |
| image       | 图片类型，可选值为 `error` `network` `search`，支持传入图片 URL | *string* | `default` |
| description | 图片下方的描述文字                                           | *string* | -         |

### Slots

| 名称        | 说明           |
| :---------- | :------------- |
| -           | 自定义底部内容 |
| image       | 自定义图标     |
| description | 自定义描述文字 |

​    

​    

## Grid 宫格

示例：

```vue
<template>
	<van-grid>
    <van-grid-item icon="ri-image-line" text="文字" />
    <van-grid-item icon="ri-image-line" text="文字" />
    <van-grid-item icon="ri-image-line" text="文字" />
    <van-grid-item icon="ri-image-line" text="文字" />
  </van-grid>
</template>
```

### Grid Props

| 参数       | 说明                                      | 类型      | 默认值     |
| :--------- | :---------------------------------------- | :-------- | :--------- |
| column-num | 列数                                      | *number*  | `4`        |
| icon-size  | 图标大小，默认单位为`px`                  | *string*  | `26px`     |
| border     | 是否显示边框                              | *boolean* | `true`     |
| center     | 是否将格子内容居中显示                    | *boolean* | `true`     |
| square     | 是否将格子固定为正方形                    | *boolean* | `false`    |
| clickable  | 是否开启格子点击反馈                      | *boolean* | `false`    |
| direction  | 格子内容排列的方向，可选值为 `horizontal` | *string*  | `vertical` |
| reverse    | 是否调换图标和文本的位置                  | *boolean* | `false`    |
| use-slot   | 是否使用自定义内容的插槽                  | *boolean* | `false`    |

### GridItem Props

| 参数       | 说明                                                         | 类型               | 默认值       |
| :--------- | :----------------------------------------------------------- | :----------------- | :----------- |
| text       | 文字                                                         | *string*           | -            |
| icon       | 图标名称或图片链接，可选值见 [Icon 组件](https://youzan.github.io/vant-weapp/#/icon) | *string*           | -            |
| icon-color | 图标颜色                                                     | *string*           | -            |
| dot        | 是否显示图标右上角小红点                                     | *boolean*          | `false`      |
| badge      | 图标右上角徽标的内容                                         | *string \| number* | -            |
| url        | 点击后跳转的链接地址                                         | *string*           | -            |
| link-type  | 链接跳转类型，可选值为 `redirectTo` `switchTab` `reLaunch`   | *string*           | `navigateTo` |

### GridItem Events

| 事件名 | 说明           | 回调参数 |
| :----- | :------------- | :------- |
| @click | 点击格子时触发 | -        |

### GridItem Slots

| 名称 | 说明                                                   |
| :--- | :----------------------------------------------------- |
| -    | 自定义宫格的所有内容，需要设置`use-slot`属性           |
| icon | 自定义图标，如果设置了`use-slot`或者`icon`属性则不生效 |
| text | 自定义文字，如果设置了`use-slot`或者`text`属性则不生效 |

​    

​    

## NavBar 导航栏

示例：

```vue
<template>
	<van-nav-bar
  title="标题"
  left-text="返回"
  right-text="按钮"
  left-arrow
  bind:click-left="onClickLeft"
  bind:click-right="onClickRight"
/>
</template>
```

### Props

| 参数                | 说明                               | 类型      | 默认值  |
| :------------------ | :--------------------------------- | :-------- | :------ |
| title               | 标题                               | *string*  | `''`    |
| left-text           | 左侧文案                           | *string*  | `''`    |
| right-text          | 右侧文案                           | *string*  | `''`    |
| left-arrow          | 是否显示左侧箭头                   | *boolean* | `false` |
| fixed               | 是否固定在顶部                     | *boolean* | `false` |
| placeholder         | 固定在顶部时是否开启占位           | *boolean* | `false` |
| border              | 是否显示下边框                     | *boolean* | `true`  |
| hover               | 是否开启点击反馈                   | *boolean* | `true`  |
| z-index             | 元素 z-index                       | *number*  | `1`     |
| safe-area-inset-top | 是否留出顶部安全距离（状态栏高度） | *boolean* | `true`  |

### Slot

| 名称  | 说明               |
| :---- | :----------------- |
| title | 自定义标题         |
| left  | 自定义左侧区域内容 |
| right | 自定义右侧区域内容 |

### Events

| 事件名 | 说明               | 参数 |
| :----- | :----------------- | :--- |
| @left  | 点击左侧按钮时触发 | -    |
| @right | 点击右侧按钮时触发 | -    |

​    

​    

# Loading 加载

示例：

```vue
<template>
	<van-loading />
	<van-loading type="spinner" />
</template>
```

### Props

| 参数      | 说明                          | 类型               | 默认值     |
| :-------- | :---------------------------- | :----------------- | :--------- |
| color     | 颜色                          | *string*           | `#c8c9cc`  |
| type      | 类型，可选值为 `spinner`      | *string*           | `circular` |
| size      | 加载图标大小，默认单位为 `px` | *string \| number* | `30`       |
| text-size | 文字大小，默认单位为为 `px`   | *string \| number* | `14`       |
| vertical  | 是否垂直排列图标和文字内容    | *boolean*          | `false`    |

### Slots

| 名称 | 说明     |
| :--- | :------- |
| -    | 加载文案 |
