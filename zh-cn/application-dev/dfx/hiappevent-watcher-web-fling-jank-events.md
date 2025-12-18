# ArkWeb抛滑丢帧事件介绍

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @pxlstrong-->
<!--Designer: @pxlstrong-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## 简介
从API version 23开始，支持订阅ArkWeb抛滑丢帧事件。页面滑动一般分为两个阶段，拖滑和抛滑。拖滑指触摸屏幕时的滑动，抛滑指在手指离开屏幕后，页面还在以一定的速度滑动。用户在使用应用的过程中，滑动web页面，如果出现抛滑丢帧的情况，并且卡顿持续时间超过一定限制（50ms），就会被定义为ArkWeb抛滑丢帧，并生成相关丢帧数据。

ArkWeb抛滑丢帧事件仅提供发生卡顿的Web组件对应的web_id，最长丢帧时长等数据，不提供卡顿日志等信息，需应用自身结合信息获取卡顿页面结合业界成熟的[DevTools工具](../web/web-debugging-with-devtools.md)复现并排查页面问题。

本文面向开发者介绍ArkWeb抛滑丢帧检测原理，以及各字段的含义和规格。如需了解如何使用HiAppEvent接口订阅系统ArkWeb抛滑丢帧检测事件，请参考以下文档。

- [订阅ArkWeb抛滑丢帧事件（ArkTS）](hiappevent-watcher-web-fling-jank-events-arkts.md)

## 检测原理

ArkWeb在渲染绘制完成之后会生成buffer，并将生成的buffer送至图形缓冲区，图形侧取出buffer进行送显。在抛滑阶段，通过检测AkrWeb前后两次与图形侧交换buffer的时间差判断是否超时异常，来判断ArkWeb侧是否发生了丢帧。

## params字段说明

ArkWeb抛滑丢帧事件信息中params属性的详细描述如下：

| 名称 | 类型 | 说明 |
| -------- | -------- | -------- |
| start_time | number | 抛滑动效开始时间，单位为ms。 |
| duration | number | 抛滑动效持续时长，单位为ms。|
| web_id | number | 发生丢帧组件对应的web_id。|
| max_app_frame_time | number | 抛滑期间最长连续丢帧时长，单位为ms。|