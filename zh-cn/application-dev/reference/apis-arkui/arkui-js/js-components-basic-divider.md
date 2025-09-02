# divider
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lanshouren-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @HelloCrease-->

>  **说明：**
>  从API version 4开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

提供分隔器组件，分隔不同内容块/内容元素。可用于列表或界面布局。

## 权限列表

无


## 子组件

不支持。


## 属性

除支持[通用属性](js-components-common-attributes.md)外，还支持如下属性：

| 名称       | 类型      | 默认值   | 必填   | 描述                   |
| -------- | ------- | ----- | ---- | -------------------- |
| vertical | boolean | false | 否    | 使用水平分割线还是垂直分割线，默认水平。 |

>  **说明：**
>  不支持focusable、disabled属性。


## 样式

仅支持如下样式：

| 名称                                | 类型             | 默认值        | 必填   | 描述                                       |
| --------------------------------- | -------------- | ---------- | ---- | ---------------------------------------- |
| margin                            | &lt;length&gt; | 0          | 否    | 使用简写属性设置所有的外边距属性，该属性可以有1到4个值。            |
| margin-[left\|top\|right\|bottom] | &lt;length&gt; | 0          | 否    | 使用简写属性设置左、上、右、下外边距属性，类型length，单位px，默认值0。 |
| color                             | &lt;color&gt;  | \#08000000 | 否    | 设置分割线颜色。                                 |
| stroke-width                      | &lt;length&gt; | 1          | 否    | 设置分割线宽度。                                 |
| display                           | string         | flex       | 否    | 确定分割线所产生的框的类型。值flex/none，默认值flex。        |
| visibility                        | string         | visible    | 否    | 是否显示分割线。不可见的框会占用布局。visible代表显示元素，hidden代表不显示元素。 |
| line-cap                          | string         | butt       | 否    | 设置分割线条的端点样式，默认为butt，可选值为：<br/>-&nbsp;butt：分割线两端为平行线；<br/>-&nbsp;round：分割线两端额外添加半圆，额外增加一个线宽的分割线长度；<br/>-&nbsp;square：分割线两端额外添加半方形，额外增加一个线宽的分割线长度； |
| flex                              | number         | -          | 否    | 规定了分割线如何适应父组件中的可用空间，用来设置组件的flex-grow。<br>仅父容器为&lt;div&gt;、&lt;list-item&gt;、&lt;tabs&gt;时生效。 |
| flex-grow                         | number         | 0          | 否    | 设置分割线的伸展因子，指定父组件容器主轴方向上剩余空间（容器本身大小减去所有flex项加起来的大小）的分配系数，0为不伸展。<br/>仅父容器为&lt;div&gt;、&lt;list-item&gt;、&lt;tabs&gt;时生效。 |
| flex-shrink                       | number         | 1          | 否    | 设置分割线的收缩因子，flex元素仅在默认宽度之和大于容器的时候才会发生收缩，0为不收缩。<br/>仅父容器为&lt;div&gt;、&lt;list-item&gt;、&lt;tabs&gt;时生效。 |
| flex-basis                        | &lt;length&gt; | -          | 否    | 设置分割线在主轴方向上的初始大小。<br>仅父容器为&lt;div&gt;、&lt;list-item&gt;、&lt;tabs&gt;时生效。 |


## 事件

不支持。


## 方法

不支持。


## 示例

```html
<!-- xxx.hml -->
<div class="container">   
  <div class="content">        
    <divider class="divider" vertical="false"></divider>    
  </div>
</div>
```

```css
/* xxx.css */
.container {    
  margin: 20px;
  flex-direction:column;
  width:100%;
  height:100%;
  align-items:center;
}
.content{    
  width:80%;
  height:40%;
  border:1px solid #000000;
  align-items: center;
  justify-content: center;
  flex-direction:column;
}
.divider {    
  margin: 10px;
  color: #ff0000ff;
  stroke-width: 3px;
  line-cap: round;
}
```

![zh-cn_image_0000001173164799](figures/zh-cn_image_0000001173164799.jpg)
