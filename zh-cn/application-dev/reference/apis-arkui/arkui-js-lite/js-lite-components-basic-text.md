# text
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--SE: @pssea-->
<!--TSE: @jiaoaozihao-->

文本，用于呈现一段信息。

> **说明：**
>
> 该组件从API version 4 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


## 子组件

不支持。


## 属性

| 名称 | 类型 | 默认值 | 必填 | 描述 |
| -------- | -------- | -------- | -------- | -------- |
| id | string | - | 否 | 组件的唯一标识。 |
| style | string | - | 否 | 组件的样式声明。 |
| class | string | - | 否 | 组件的样式类，用于引用样式表。 |
| ref | string | - | 否 | 用来指定指向子元素的引用信息，该引用将注册到父组件的$refs&nbsp;属性对象上。 |


## 事件

| 名称 | 参数 | 描述 |
| -------- | -------- | -------- |
| click | - | 点击动作触发该事件。 |
| longpress | - | 长按动作触发该事件。 |
| swipe<sup>5+</sup> | [SwipeEvent](js-lite-common-events.md) | 组件上快速滑动后触发。 |


## 样式

| 名称 | 类型 | 默认值 | 必填 | 描述 |
| -------- | -------- | -------- | -------- | -------- |
| color | &lt;color&gt; | \#ffffff | 否 | 设置文本的颜色。 |
| font-size | &lt;length&gt; | 30px | 否 | 设置文本的尺寸。<br/> |
| letter-spacing | &lt;length&gt; | 2px | 否 | 设置文本的字符间距。 |
| text-align | string | left | 否 | 设置文本的文本对齐方式，可选值为：<br/>-&nbsp;left：文本左对齐；<br/>-&nbsp;center：文本居中对齐；<br/>-&nbsp;right：文本右对齐； |
| text-overflow | string | clip | 否 | 可选值为：<br/>-&nbsp;clip：将文本根据父容器大小进行裁剪显示；<br/>-&nbsp;ellipsis：根据父容器大小显示，显示不下的文本用省略号代替。 |
| font-family | string | SourceHanSansSC-Regular | 否 | 字体。目前仅支持SourceHanSansSC-Regular&nbsp;字体。 |
| width | &lt;length&gt;&nbsp;\|&nbsp;&lt;percentage&gt;<sup>5+</sup> | 0px | 否 | 设置组件自身的宽度。<br/>单位：px<br/>未设置时组件宽度默认为0。 |
| height | &lt;length&gt;&nbsp;\|&nbsp;&lt;percentage&gt;<sup>5+</sup> | 0px | 否 | 设置组件自身的高度。<br/>单位：px<br/>未设置时组件高度默认为0。 |
| padding | &lt;length&gt; | 0 | 否 | 使用简写属性设置所有的内边距属性。<br/>&nbsp;&nbsp;该属性可以有1到4个值：<br/>-&nbsp;指定一个值时，该值指定四个边的内边距。<br/>-&nbsp;指定两个值时，第一个值指定上下两边的内边距，第二个指定左右两边的内边距。<br/>-&nbsp;指定三个值时，第一个指定上边的内边距，第二个指定左右两边的内边距，第三个指定下边的内边距。<br/>-&nbsp;指定四个值时分别为上、右、下、左边的内边距（顺时针顺序）。 |
| padding-[left\|top\|right\|bottom] | &lt;length&gt; | 0 | 否 | 设置左、上、右、下内边距属性。 |
| margin | &lt;length&gt;&nbsp;\|&nbsp;&lt;percentage&gt;<sup>5+</sup> | 0 | 否 | 使用简写属性设置所有的外边距属性，该属性可以有1到4个值。<br/>-&nbsp;只有一个值时，这个值会被指定给全部的四个边。<br/>-&nbsp;两个值时，第一个值被匹配给上和下，第二个值被匹配给左和右。<br/>-&nbsp;三个值时，第一个值被匹配给上,&nbsp;第二个值被匹配给左和右，第三个值被匹配给下。<br/>-&nbsp;四个值时，会依次按上、右、下、左的顺序匹配&nbsp;(即顺时针顺序)。 |
| margin-[left\|top\|right\|bottom] | &lt;length&gt;&nbsp;\|&nbsp;&lt;percentage&gt;<sup>5+</sup> | 0 | 否 | 设置左、上、右、下外边距属性。 |
| border-width | &lt;length&gt; | 0 | 否 | 使用简写属性设置元素的所有边框宽度。 |
| border-color | &lt;color&gt; | black | 否 | 使用简写属性设置元素的所有边框颜色。 |
| border-radius | &lt;length&gt; | - | 否 | border-radius属性是设置元素的外边框圆角半径。 |
| background-color | &lt;color&gt; | - | 否 | 设置背景颜色。 |
| opacity<sup>5+</sup> | number | 1 | 否 | 元素的透明度，取值范围为0到1，1表示为不透明，0表示为完全透明。 |
| display | string | flex | 否 | 确定一个元素所产生的框的类型，可选值为：<br/>-&nbsp;flex：弹性布局。<br/>-&nbsp;none：不渲染此元素。 |
| [left\|top] | &lt;length&gt;&nbsp;\|&nbsp;&lt;percentage&gt;<sup>6+</sup> | - | 否 | left\|top确定元素的偏移位置。<br/>-&nbsp;left属性规定元素的左边缘。该属性定义了定位元素左外边距边界与其包含块左边界之间的偏移。<br/>-&nbsp;top属性规定元素的顶部边缘。该属性定义了一个定位元素的上外边距边界与其包含块上边界之间的偏移。 |
| line-height<sup>10+</sup> | number | 0px | 否 | 设置文本的行高。<br/>单位：px<br/>未设置时文本行高默认为适应性行高。 |

## 示例

```html
<!-- xxx.hml -->
<div class="container">
    <text class="title">
        Hello {{ title }}
    </text>
</div>
```

```CSS
/* xxx.css */
.container {
    width: 100%;
    height: 100%;
    justify-content: center;
    align-items: center;
}

.title {
    width: 100px;
    font-size: 30px;
    text-align: center;
    color: red;
}
```

```javascript
// xxx.js
export default {
    data: {
        title: ""
    },
    onInit() {
        this.title = "World";
    }
}
```

![text](figures/text-lite.png)