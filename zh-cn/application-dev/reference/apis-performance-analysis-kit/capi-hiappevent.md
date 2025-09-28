# HiAppEvent

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @liujiaxing2024-->
<!--Designer: @junjie_shi-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## 概述

HiAppEvent模块提供应用事件打点功能。为应用程序提供事件打点功能，记录运行过程中上报的故障事件、统计事件、安全事件和用户行为事件。基于事件信息，开发者可以分析应用的运行状态。

**起始版本：** 8
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [hiappevent.h](capi-hiappevent-h.md) | HiAppEvent模块的应用事件打点函数定义。在执行应用事件打点之前，开发者必须先构造一个参数列表对象来存储输入的事件参数，并指定事件领域、事件名称和事件类型。<p>事件领域：用于标识事件打点的领域的字符串。<p>事件名称：用于标识事件打点的名称的字符串。<p>事件类型：故障、统计、安全、行为。<p>参数列表：用于存储事件参数的链表，每个参数由参数名和参数值组成。 |
| [hiappevent_cfg.h](capi-hiappevent-cfg-h.md) | 定义事件打点配置函数的所有配置项名称。如果开发者想要对应用事件打点功能进行配置，开发者可以直接使用配置项常量。 |
| [hiappevent_event.h](capi-hiappevent-event-h.md) | 定义所有预定义事件的事件名称。除了与特定应用关联的自定义事件之外，开发者还可以使用预定义事件进行打点。 |
| [hiappevent_param.h](capi-hiappevent-param-h.md) | 定义所有预定义事件的参数名称。除了与特定应用关联的自定义事件之外，开发者还可以使用预定义事件进行打点。 |
