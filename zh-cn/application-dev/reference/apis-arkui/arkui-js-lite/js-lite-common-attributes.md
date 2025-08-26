# 通用属性
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->


## 常规属性

常规属性指的是组件普遍支持的用来设置组件基本标识和外观显示特征的属性。

| 名称 | 类型 | 必填 | 描述 |
| -------- | -------- | -------- | -------- |
| id | string | 否 | 组件的唯一标识。 |
| style | string | 否 | 组件的样式声明。 |
| class | string | 否 | 组件的样式类，用于引用样式表。 |
| ref | string | 否 | 用来指定指向子元素的引用信息，该引用将注册到父组件的$refs&nbsp;属性对象上。 |


## 渲染属性

组件普遍支持的用来设置组件是否渲染的属性。

| 名称 | 类型 | 描述 |
| -------- | -------- | -------- |
| for | Array | 根据设置的数据列表，展开当前元素。 |
| if | boolean | 根据设置的boolean值，添加或移除当前元素。 |
| show | boolean | 根据设置的boolean值，显示或隐藏当前元素。 |

> **说明：**
>
> 属性和样式不能混用，不能在属性字段中进行样式设置。
