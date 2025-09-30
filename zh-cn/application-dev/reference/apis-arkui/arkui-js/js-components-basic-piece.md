# piece
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @HelloCrease-->

 一种块状的入口，可包含图片和文本，常用于展示收件人。例如，邮件收件人或信息收件人。 

>  **说明：**
>  从API version 5开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


## 子组件

无


## 属性

除支持[通用属性](js-components-common-attributes.md)外，还支持如下属性：

| 名称     | 类型    | 必填 | 描述                                                         |
| -------- | ------- | ---- | ------------------------------------------------------------ |
| content  | string  | 是   | 操作块文本内容。                                             |
| closable | boolean | 否   | 设置当前操作块是否显示删除图标，当显示删除图标时，点击删除图标会触发close事件。<br/>true表示显示删除图标，false表示不显示删除图标。默认为false。|
| icon     | string  | 否   | 操作块删除图标的url，支持本地路径。                          |


## 样式

支持[通用样式](js-components-common-styles.md)。

>  **说明：**
>  文本和图片默认在整个piece组件中居中。


## 事件

除支持[通用事件](js-components-common-events.md)外，还支持如下事件：

| 名称    | 参数   | 描述                                  |
| ----- | ---- | ----------------------------------- |
| close | -    | 当piece组件点击删除图标触发，此时可以通过渲染属性if删除该组件。 |

## 方法

支持[通用方法](js-components-common-methods.md)。


## 示例

```html
<!-- xxx.hml-->
<div class="container" >
  <piece if="{{first}}" content="example"></piece>
  <piece if="{{second}}" content="example" closable="true" onclose="closeSecond"></piece>
</div>
```

```css
/* xxx.css */
.container {
  width: 100%;
  height: 100%;
  align-items: center;
  justify-content: center;
}
```

```js
// xxx.js
export default {
  data: {
    first: true,
    second: true
  },
  closeSecond(e) {
    this.second = false;
  }
}
```

![zh-cn_image_0000001177428498](figures/zh-cn_image_0000001177428498.gif)
