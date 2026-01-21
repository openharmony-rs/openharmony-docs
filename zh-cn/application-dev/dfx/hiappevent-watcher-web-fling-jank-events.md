# ArkWeb抛滑丢帧事件介绍

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @pxlstrong-->
<!--Designer: @pxlstrong-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## 简介
[ArkWeb](../web/web-component-overview.md)提供了Web组件，用于在应用程序中显示Web页面内容，为开发者提供了丰富的控制Web页面能力。页面滑动一般分为两个阶段：拖滑和抛滑。拖滑指触摸屏幕时的滑动。抛滑指在手指离开屏幕后，页面仍以一定速度滑动。从API version 23开始，支持订阅ArkWeb抛滑丢帧事件，用户在使用应用时滑动web页面，如果出现抛滑丢帧且卡顿持续时间超过50ms及以上，就会被定义为ArkWeb抛滑丢帧，并生成相关丢帧数据。

本文面向开发者介绍ArkWeb抛滑丢帧事件检测原理，以及各字段的含义和规格。如需了解如何使用HiAppEvent接口订阅ArkWeb抛滑丢帧事件，请参考以下文档。

- [订阅ArkWeb抛滑丢帧事件（ArkTS）](hiappevent-watcher-web-fling-jank-events-arkts.md)

> **说明**
>
> ArkWeb抛滑丢帧事件仅提供发生卡顿的Web组件对应的web_id，最长丢帧时长及其他相关数据，不提供卡顿日志等信息。开发者可以借助web_id，参考“订阅ArkWeb抛滑丢帧事件（ArkTS）”文件中的示例代码获取到发生丢帧的网页地址，再结合业界成熟的[DevTools工具](../web/web-debugging-with-devtools.md)复现并排查根因。
>
> 从API version 23开始，ArkWeb抛滑丢帧事件支持在[应用分身](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/app-clone)、原子化服务及[输入法应用](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/inputmethod-application-guide)场景下使用 HiAppEvent 进行订阅。

## 检测原理

ArkWeb在渲染绘制完成之后会生成buffer，并将生成的buffer送至图形缓冲区，图形侧取出buffer进行送显。在抛滑阶段，通过检测ArkWeb前后两次与图形侧交换buffer的时间差判断是否超时异常，来判断ArkWeb侧是否发生了丢帧。

## params字段说明

ArkWeb抛滑丢帧事件信息中params属性的详细描述如下：

| 名称 | 类型 | 说明 |
| -------- | -------- | -------- |
| start_time | number | 抛滑动效开始时间，为一个时间戳。 |
| duration | number | 抛滑动效持续时长，单位为ms。|
| web_id | number | 发生丢帧组件对应的web_id。|
| max_app_frame_time | number | 抛滑期间最长连续丢帧时长，单位为ms。|