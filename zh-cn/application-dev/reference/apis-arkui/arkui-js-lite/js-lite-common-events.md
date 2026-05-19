# 通用事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

## 事件说明

相对于私有事件，大部分组件都可以绑定如下事件。

| 名称 | 参数 | 描述 |
| -------- | -------- | -------- |
| click | - | 点击动作触发该事件。 |
| longpress | - | 长按动作触发该事件。 |
| swipe<sup>5+</sup> | SwipeEvent | 组件上快速滑动后触发。 |

## BaseEvent

基础事件类型。

| 属性                  | 类型                   | 说明                                     |
| --------------------- | ---------------------- | ---------------------------------------- |
| type                  | string                 | 当前事件的类型，比如click、longpress等。 |
| timestamp             | number                 | 该事件触发时的时间戳。<br>单位：ms                   |
| deviceId<sup>8+</sup> | number                 | 触发该事件的设备ID信息。                 |
| target<sup>12+</sup>   | [Target](../arkui-js/js-components-common-events.md#target对象6) | 触发该事件的目标对象。                   |

## SwipeEvent

继承自[BaseEvent](#baseevent)。

| 属性 | 类型 | 说明 |
| -------- | -------- | -------- |
| direction | string | 滑动方向，可能值有：<br/>1.&nbsp;left：向左滑动；<br/>2.&nbsp;right：向右滑动；<br/>3.&nbsp;up：向上滑动；<br/>4.&nbsp;down：向下滑动。 |
