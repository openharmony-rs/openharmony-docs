# HiAppEvent

## 概述

提供应用事件日志记录功能。为应用提供事件日志功能，记录故障、统计、安全、用户行为等运行过程中上报的事件。通过事件信息，可以分析应用程序的运行情况。

**起始版本：** 8
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [hiappevent.h](capi-hiappevent-h.md) | HiAppEvent模块为应用开发者提供的事件订阅和事件打点函数定义。在执行应用事件打点之前，开发者必须先构造一个参数列表对象来存储输入的事件参数，并指定事件领域、事件名称和事件类型。<p>事件领域：用于标识事件打点的领域的字符串。<p>事件名称：用于标识事件打点的名称的字符串。<p>事件类型：故障、统计、安全、行为。<p>参数列表：用于存储事件参数的链表，每个参数由参数名和参数值组成。 |
| [hiappevent_cfg.h](capi-hiappevent-cfg-h.md) | 定义事件日志配置函数的所有配置项名称。如果要配置事件日志功能，可以直接使用配置项常量。示例代码:<pre>bool res = OH_HiAppEvent_Configure(MAX_STORAGE, "100M");</pre> |
| [hiappevent_event.h](capi-hiappevent-event-h.md) | 定义所有预定义事件的事件名称。除了与特定应用关联的自定义事件之外，您还可以使用预定义事件进行日志记录。示例代码：<pre>ParamList list = OH_HiAppEvent_CreateParamList();OH_HiAppEvent_AddInt32Param(list, PARAM_USER_ID, 123);int res = OH_HiAppEvent_Write("user_domain", EVENT_USER_LOGIN, BEHAVIOR, list);OH_HiAppEvent_DestroyParamList(list);</pre> |
| [hiappevent_param.h](capi-hiappevent-param-h.md) | 定义所有预定义事件的param名称。除了与特定应用关联的自定义事件之外，您还可以使用预定义事件进行日志记录。示例代码：<pre>ParamList list = OH_HiAppEvent_CreateParamList();OH_HiAppEvent_AddInt32Param(list, PARAM_USER_ID, 123);int res = OH_HiAppEvent_Write("user_domain", EVENT_USER_LOGIN, BEHAVIOR, list);OH_HiAppEvent_DestroyParamList(list);</pre> |
