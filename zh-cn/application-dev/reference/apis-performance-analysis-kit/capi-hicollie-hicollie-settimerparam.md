# HiCollie_SetTimerParam

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct HiCollie_SetTimerParam {...} HiCollie_SetTimerParam
```

## 概述

定义OH_HiCollie_SetTimer函数的输入参数，用于设置定时器监控任务的名称、任务超时时间阈值、超时回调函数及执行动作标志。<br> 使用场景：适用于需要监控任务执行时间的场景，帮助开发者监控和处理任务超时问题。

**起始版本：** 18

**相关模块：** [HiCollie](capi-hicollie.md)

**所在头文件：** [hicollie.h](capi-hicollie-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char *name | timer任务名称。任务名称不可为空。 |
| unsigned int timeout | 任务超时时间阈值，单位：s，取值为大于0的正整数。当任务执行时间超过该阈值时，将触发超时处理机制。建议根据实际业务场景设置。 |
| [OH_HiCollie_Callback](capi-hicollie-h.md#oh_hicollie_callback) func | 超时发生时执行的回调函数。 |
| void *arg | 回调函数的参数。 |
| [HiCollie_Flag](capi-hicollie-h.md#hicollie_flag) flag | 超时发生时执行的动作，参考[HiCollie_Flag](capi-hicollie-h.md#hicollie_flag)。 |


