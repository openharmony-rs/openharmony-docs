# ArkWeb抛滑丢帧事件介绍

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @pxlstrong-->
<!--Designer: @pxlstrong-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## 简介
从API version 23开始，支持订阅ArkWeb抛滑丢帧事件。页面滑动一般分为两个阶段，拖滑和抛滑。拖滑指触摸屏幕时的滑动，抛滑指在手指离开屏幕后，页面还在以一定的速度滑动。用户在使用应用的过程中，滑动web页面，如果出现抛滑丢帧的情况，并且卡顿持续时间超过一定限制（50ms），就会被定义为ArkWeb抛滑丢帧，并生成相关丢帧数据。

> **说明**
>
>ArkWeb抛滑丢帧事件仅提供发生卡顿的Web组件对应的web_id，最长丢帧时长等数据，不提供卡顿日志等信息，需应用自身结合信息获取卡顿页面结合业界成熟的[DevTools工具](../web/web-debugging-with-devtools.md)复现并排查页面问题。
>
> 从API version 23开始，ArkWeb抛滑丢帧事件支持在[应用分身](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/app-clone)场景下使用 HiAppEvent 进行订阅，支持在原子化服务场景下使用HiAppEvent 进行订阅，支持在[输入法应用](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/inputmethod-application-guide)场景下使用 HiAppEvent 进行订阅。



## 检测原理

ArkWeb在渲染绘制完成之后会生成buffer，并将生成的buffer送至图形缓冲区，图形侧取出buffer进行送显。在抛滑阶段，通过检测AkrWeb前后两次与图形侧交换buffer的时间差判断是否超时异常，来判断ArkWeb侧是否发生了丢帧。

## 接口说明

开发者可以通过HiAppEvent提供接口订阅ArkWeb抛滑丢帧事件“SCROLL_ARKWEB_FLING_JANK”，系统检测到ArkWeb抛滑卡顿后，会抓取维测信息通过HiAppEvent将ArkWeb抛滑丢帧数据回调给应用进程。

- [订阅ArkWeb抛滑丢帧事件（ArkTS）](hiappevent-watcher-web-fling-jank-events-arkts.md)

## params字段说明

ArkWeb抛滑丢帧事件信息中params属性的详细描述如下：

| 名称 | 类型 | 说明 |
| -------- | -------- | -------- |
| start_time | number | 抛滑动效开始时间，单位为ms。 |
| duration | number | 抛滑动效持续时长，单位为ms。|
| web_id | number | 发生丢帧组件对应的web_id。|
| max_app_frame_time | number | 抛滑期间最长连续丢帧时长，单位为ms。|