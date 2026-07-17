# hiappevent_event.h

## 概述

定义所有预定义事件的事件名称。除了与特定应用关联的自定义事件之外，您还可以使用预定义事件进行日志记录。示例代码：<pre>ParamList list = OH_HiAppEvent_CreateParamList();OH_HiAppEvent_AddInt32Param(list, PARAM_USER_ID, 123);int res = OH_HiAppEvent_Write("user_domain", EVENT_USER_LOGIN, BEHAVIOR, list);OH_HiAppEvent_DestroyParamList(list);</pre>

**库：** libhiappevent_ndk.z.so

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**起始版本：** 8

**相关模块：** [HiAppEvent](capi-hiappevent.md)

## 汇总

### 宏定义

| 名称 | 描述 |
| -- | -- |
| EVENT_USER_LOGIN "hiappevent.user_login" | 用户登录事件。<br>**起始版本：** 8 |
| EVENT_USER_LOGOUT "hiappevent.user_logout" | 用户登出事件。<br>**起始版本：** 8 |
| EVENT_DISTRIBUTED_SERVICE_START "hiappevent.distributed_service_start" | 分布式服务事件。<br>**起始版本：** 8 |
| EVENT_APP_CRASH "APP_CRASH" | 崩溃事件。<br>**起始版本：** 12 |
| EVENT_APP_FREEZE "APP_FREEZE" | 应用冻屏事件。<br>**起始版本：** 12 |
| EVENT_APP_LAUNCH "APP_LAUNCH" | 启动耗时事件。<br>**起始版本：** 12 |
| EVENT_SCROLL_JANK "SCROLL_JANK" | 滑动丢帧事件。<br>**起始版本：** 12 |
| EVENT_CPU_USAGE_HIGH "CPU_USAGE_HIGH" | CPU高负载事件。<br>**起始版本：** 12 |
| EVENT_BATTERY_USAGE "BATTERY_USAGE" | 24h功耗器件分解统计事件。<br>**起始版本：** 12 |
| EVENT_RESOURCE_OVERLIMIT "RESOURCE_OVERLIMIT" | 资源泄漏事件。<br>**起始版本：** 12 |
| EVENT_ADDRESS_SANITIZER "ADDRESS_SANITIZER" | 地址越界事件。<br>**起始版本：** 12 |
| EVENT_MAIN_THREAD_JANK "MAIN_THREAD_JANK" | 主线程超时事件。<br>**起始版本：** 12 |
| EVENT_MAIN_THREAD_JANK_V2 "MAIN_THREAD_JANK_V2" | 用于设置主线程超时事件配置策略。<br>**起始版本：** 22 |
| EVENT_APP_HICOLLIE "APP_HICOLLIE" | app hicollie event.<br>**起始版本：** 18 |
| DOMAIN_OS "OS" | OS作用域。<br>**起始版本：** 12 |
| EVENT_APP_KILLED "APP_KILLED" | app killed event.<br>**起始版本：** 20 |
| EVENT_AUDIO_JANK_FRAME "AUDIO_JANK_FRAME" | audio jank frame event.<br>**起始版本：** 21 |
| OH_EVENT_APP_FREEZE_WARNING "APPFREEZE_WARNING" | 应用冻屏告警事件。<br>**起始版本：** 26.0.0 |

