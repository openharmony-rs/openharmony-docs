# tab-content
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--SE: @yangfan229-->
<!--TSE: @lxl007-->

>  **说明：**
> 从API version 4开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

&lt;[tabs](js-components-container-tabs.md)&gt;的子组件，用来展示tab的内容区，高度默认充满tabs剩余空间，子组件排列方式为横向排列，当作为容器组件的子元素时在主轴方向需要设置tab-content的确定长度，否则无法显示。tab-content组件不支持内容过长时页面的滑动，如需页面滑动，可嵌套List使用。

## 权限列表

无


## 子组件

支持。


## 属性

除支持[通用属性](js-components-common-attributes.md)外，还支持如下属性：

| 名称 | 类型 | 必填 | 描述 |
| -------- | -------- | -------- | -------- |
| scrollable | boolean | &nbsp;&nbsp;否&nbsp;&nbsp; | 是否可以通过左右滑动进行页面切换。默认为true，设置为false后，页面的切换只能通过tab-bar的点击实现。 |


## 样式

支持[通用样式](js-components-common-styles.md)。


## 事件

支持[通用事件](js-components-common-events.md)。


## 示例

详见[tabs示例](js-components-container-tabs.md#示例)。
