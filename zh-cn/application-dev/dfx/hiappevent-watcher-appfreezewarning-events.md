# 应用冻屏告警事件介绍
<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

## 简介

从版本26.0.0开始，应用运行过程中，若仅触发THREAD_BLOCK_3S、LIFECYCLE_HALF_TIMEOUT这类[应用冻屏事件](appfreeze-guidelines.md#检测原理)中的告警事件，系统将统一判定为应用冻屏告警。针对该类异常场景，系统会提供应用冻屏告警检测、维测日志抓取及日志上报能力，帮助开发者提前预警风险、定位潜在的冻屏卡死问题。

本文面向开发者介绍AppFreezeWarning（应用冻屏告警）检测原理，以及各字段的含义和规格。如需了解如何使用HiAppEvent接口订阅应用冻屏告警事件，请参考以下文档。目前提供ArkTS和C/C++两种接口，按需选择。

- [订阅应用冻屏告警事件（ArkTS）](hiappevent-watcher-appfreezewarning-events-arkts.md)。

- [订阅应用冻屏告警事件（C/C++）](hiappevent-watcher-appfreezewarning-events-ndk.md)。

> **说明：**
>
> 应用冻屏告警事件支持在[应用分身](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/app-clone)场景、原子化服务场景、[输入法应用](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/inputmethod-application-guide)场景下使用 HiAppEvent 进行订阅。

## 检测原理

详见[AppFreeze（应用冻屏）检测原理](appfreeze-guidelines.md#检测原理)中的告警检测事件说明，如THREAD_BLOCK_3S告警事件、LIFECYCLE_HALF_TIMEOUT告警事件。

## 事件字段说明

### params字段说明

应用冻屏告警事件信息中params属性的详细描述如下：

| 名称 | 类型 | 说明 |
| -------- | -------- | -------- |
| time | number | 事件触发时间，单位为ms。 |
| foreground | boolean | 应用是否处于前台状态。true表示应用处于前台；false表示应用处于后台。 |
| bundle_version | string | 应用版本。 |
| bundle_version_code | number | 应用版本字符串。 |
| bundle_name | string | 应用名称。 |
| process_name | string | 应用的进程名称。 |
| pid | number | 应用的进程ID。 |
| uid | number | 应用的用户ID。 |
| exception | object | 异常信息，详见[exception字段说明](#exception字段说明)。 |
| hilog | string[] | 日志信息。当生成应用无响应事件日志时，从hilog缓冲区中获取最多1000行故障进程日志信息。 |
| event_handler | string[] | 主线程未处理消息。 |
| peer_binder | string[] | binder调用信息。 |
| threads | object[] | 全量线程调用栈，详见[thread字段说明](#thread字段说明)。 |
| memory | object | 内存信息，详见[memory字段说明](#memory字段说明)。 |
| process_life_time | number | 故障进程存活时间，单位为s。 |
| app_running_unique_id | string | 应用运行时唯一关联的ID。 |

### exception字段说明

| 名称 | 类型 | 说明 |
| -------- | -------- | -------- |
| name | string | 异常类型 |
| message | string | 异常原因 |

### thread字段说明

| 名称 | 类型 | 说明 |
| -------- | -------- | -------- |
| thread_name | string | 线程名。 |
| tid | number | 线程ID。 |
| frames | object[] | 线程调用栈，详见[frame字段说明](#frame字段说明)。 |
| state | string | 线程运行状态。读取自/proc/pid/stat的state的值。 |
| utime | number | 线程在用户态下消耗的CPU的嘀嗒数。读取自/proc/pid/stat的utime的值。 |
| stime | number | 线程在内核态下消耗的CPU的嘀嗒数。读取自/proc/pid/stat的stime的值。 |
| priority | number | 实时优先级。读取自/proc/pid/stat的priority的值。 |
| nice | number | 静态优先级。读取自/proc/pid/stat的nice的值。 |
| clk | number | 每秒的时钟嘀嗒次数。使用sysconf(_SC_CLK_TCK)获取，获取失败时使用默认值100。通过嘀嗒数除以该值可以计算得到运行时间（单位：秒）。 |

### frame字段说明

**Native帧frame字段说明**

| 名称 | 类型 | 说明 |
| -------- | -------- | -------- |
| symbol | string | 函数名称。**名称长度超过256字节时超出部分将被删除，防止超长字符串引起未知问题。** |
| file | string | 文件名。 |
| buildId | string | 文件唯一标识。**文件可能没有buildId**。 |
| pc | string | 程序执行的指令在文件内的偏移十六进制字节数。 |
| offset | number | 程序执行的指令在函数内偏移字节数。 |

详细说明请参见[调用栈帧内容说明](cppcrash-guidelines.md#一般故障场景日志规格)。

**Js帧frame字段说明**

| 名称 | 类型 | 说明 |
| -------- | -------- | -------- |
| file | string | 文件名 |
| packageName | string | 模块的包名 |
| symbol | string | 函数名称 |
| line | number | 代码行号 |
| column | number | 代码列号 |

详细说明请参见[JS混合栈帧内容说明](cppcrash-guidelines.md#一般故障场景日志规格)。

### memory字段说明

| 名称 | 类型 | 说明 |
| -------- | -------- | -------- |
| rss | number | 进程实际占用内存大小，单位为KB。|
| vss | number | 进程向系统申请的虚拟内存大小，单位为KB。|
| sys_free_mem | number | 空闲内存大小，单位为KB。|
| sys_avail_mem | number | 可用内存大小，单位为KB。|
| sys_total_mem | number | 总内存大小，单位为KB。|
| vm_heap_total_size | number | 主虚拟机总堆内存大小，单位为KB。 |
| vm_heap_used_size | number | 主虚拟机的生命周期过程中，持续统计存活对象的大小，单位为KB。|
