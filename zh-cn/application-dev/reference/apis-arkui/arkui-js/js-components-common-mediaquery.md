# 媒体查询
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lanshouren-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @HelloCrease-->

>  **说明：**
>
>  - 从API version 4开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
>  - media属性值默认为设备的真实尺寸大小、物理像素和真实的屏幕分辨率。请勿与以720px为基准的项目配置宽度px混淆。


媒体查询（Media Query）在移动设备上应用十分广泛，开发者经常需要根据设备的大致类型或者特定的特征和设备参数（例如屏幕分辨率）来修改应用的样式。为此媒体查询提供了如下功能：


1. 针对设备和应用的属性信息，可以设计出相匹配的布局样式。

2. 当屏幕发生动态改变时（比如分屏、横竖屏切换），应用页面布局同步更新。


## CSS语法规则

使用@media来引入查询语句，具体规则如下：

```
@media [media-type] [and|not|only] [(media-feature)] {
  CSS-Code;
}
```

@media screen and (round-screen: true) { … } ： 当设备屏幕是圆形时条件成立

@media (max-height: 800) { … } ：范围查询，CSS level 3 写法

@media (height &lt;= 800) { … } ：范围查询，CSS level 4 写法，与CSS level3写法等价

@media screen and (device-type: tv) or (resolution &lt; 2) { … } ： 同时包含媒体类型和多个媒体特征的多条件复杂语句查询


## 页面中引用资源

通过@import方式引入媒体查询，具体使用方法如下：

```
@import url [media-type] [and|not|only] [(media-feature)];
```

例如：

```
@import '../common/style.css' screen and (min-width: 600) and (max-width: 1200);
```


## 媒体类型

| 类型     | 说明             |
| ------ | -------------- |
| screen | 按屏幕相关参数进行媒体查询。 |


## 媒体逻辑操作

媒体逻辑操作符：and、or、not、only用于构成复杂媒体查询，也可以通过comma（,）将其组合起来，详细解释说明如下表。

**表1** 媒体逻辑操作符

| 类型       | 说明                                       |
| -------- | ---------------------------------------- |
| and      | 将多个媒体特征（Media&nbsp;Feature）以“与”的方式连接成一个媒体查询，只有当所有媒体特征都为true，查询条件成立。另外，它还可以将媒体类型和媒体功能结合起来。<br/>例如：screen&nbsp;and&nbsp;(device-type:&nbsp;wearable)&nbsp;and&nbsp;(max-height:&nbsp;600)&nbsp;表示当设备类型是智能穿戴同时应用的最大高度小于等于600个像素单位时成立。 |
| not      | 取反媒体查询结果，媒体查询结果不成立时返回true，否则返回false。在媒体查询列表中应用not，则not仅取反应用它的媒体查询。<br/>例如：not&nbsp;screen&nbsp;and&nbsp;(min-height:&nbsp;50)&nbsp;and&nbsp;(max-height:&nbsp;600)&nbsp;表示当应用高度小于50个像素单位或者大于600个像素单位时成立。<br/>使用not运算符时必须指定媒体类型。 |
| only     | 当整个表达式都匹配时，才会应用选择的样式，可以应用在防止某些较早的版本的浏览器上产生歧义的场景。一些较早版本的浏览器对于同时包含了媒体类型和媒体特征的语句会产生歧义，比如：<br/>screen&nbsp;and&nbsp;(min-height:&nbsp;50)<br/>老版本浏览器会将这句话理解成screen，从而导致仅仅匹配到媒体类型（screen），就应用了指定样式，使用only可以很好地规避这种情况。<br/>使用only时必须指定媒体类型。 |
| ,(comma) | 将多个媒体特征以“或”的方式连接成一个媒体查询，如果存在结果为true的媒体特征，则查询条件成立。其效果等同于or运算符。<br/>例如：screen&nbsp;and&nbsp;(min-height:&nbsp;1000),&nbsp;&nbsp;（round-screen：true）&nbsp;表示当应用高度大于等于1000个像素单位或者设备屏幕是圆形时，条件成立。 |
| or       | 将多个媒体特征以“或”的方式连接成一个媒体查询，如果存在结果为true的媒体特征，则查询条件成立。<br/>例如：screen&nbsp;and&nbsp;(max-height:&nbsp;1000)&nbsp;or&nbsp;&nbsp;（round-screen：true）表示当应用高度小于等于1000个像素单位或者设备屏幕是圆形时，条件成立。 |

在MediaQuery Level 4中引入了范围查询，使其能够使用max-，min-的同时，也支持了&lt;=，&gt;=，&lt;，&gt;操作符。

**表2** 媒体逻辑范围操作符

| 类型    | 说明                                       |
| ----- | ---------------------------------------- |
| &lt;= | 小于等于，例如：screen&nbsp;and&nbsp;(height&nbsp;&lt;=&nbsp;50)。 |
| &gt;= | 大于等于，例如：screen&nbsp;and&nbsp;(height&nbsp;&gt;=&nbsp;600)。 |
| &lt;  | 小于，例如：screen&nbsp;and&nbsp;(height&nbsp;&lt;&nbsp;50)。 |
| &gt;  | 大于，例如：screen&nbsp;and&nbsp;(height&nbsp;&gt;&nbsp;600)。 |


## 媒体特征

| 类型                     | 说明                                       |
| ---------------------- | ---------------------------------------- |
| height                 | 应用页面显示区域的高度。                             |
| min-height             | 应用页面显示区域的最小高度。                           |
| max-height             | 应用页面显示区域的最大高度。                           |
| width                  | 应用页面显示区域的宽度。                             |
| min-width              | 应用页面显示区域的最小宽度。                           |
| max-width              | 应用页面显示区域的最大宽度。                           |
| resolution             | 设备的分辨率，支持dpi，dppx和dpcm单位。其中：<br/>-&nbsp;dpi表示每英寸中物理像素个数，1dpi≈0.39dpcm；<br/>-&nbsp;dpcm表示每厘米上的物理像素个数，1dpcm&nbsp;≈&nbsp;2.54dpi；<br/>-&nbsp;dppx表示每个px中的物理像素数（此单位按96px=1英寸为基准，与页面中的px单位计算方式不同），1dppx&nbsp;=&nbsp;96dpi。 |
| min-resolution         | 设备的最小分辨率。                                |
| max-resolution         | 设备的最大分辨率。                                |
| orientation            | 屏幕的方向。<br/>可选值：<br/>-&nbsp;orientation:&nbsp;portrait（设备竖屏）<br/>-&nbsp;orientation:&nbsp;landscape（设备横屏） |
| aspect-ratio           | 应用页面显示区域的宽度与高度的比值。<br/>例如：aspect-ratio:1/2 |
| min-aspect-ratio       | 应用页面显示区域的宽度与高度的最小比值。                     |
| max-aspect-ratio       | 应用页面显示区域的宽度与高度的最大比值。                     |
| device-height          | 设备的高度。                                   |
| min-device-height      | 设备的最小高度。                                 |
| max-device-height      | 设备的最大高度。                                 |
| device-width           | 设备的宽度。                                   |
| min-device-width       | 设备的最小宽度。                                 |
| max-device-width       | 设备的最大宽度。                                 |
| round-screen           | 屏幕类型，圆形屏幕为true，&nbsp;非圆形屏幕为&nbsp;false。  |
| dark-mode<sup>6+</sup> | 系统为深色模式时为true，否则为false。                  |


## 通用媒体特征示例代码

多个.container中定义的属性个数及类型必须保持一致，否则会导致显示异常。

```html
<!-- xxx.hml -->
<div>
  <div class="container">
    <text class="title">Hello World</text>
  </div>
</div>
```

```css
/* xxx.css */
.container {
  width: 300px;
  height: 600px;
  background-color: #008000;
}
@media (device-type: tv) {
  .container {
    width: 500px;
    height: 500px;
    background-color: #fa8072;
  }
} 
@media (device-type: wearable) {
  .container {
    width: 300px;
    height: 300px;
    background-color: #008b8b;
  }
} 
```
