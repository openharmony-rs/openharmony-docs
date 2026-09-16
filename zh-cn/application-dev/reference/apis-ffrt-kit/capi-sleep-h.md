# sleep.h

<!--Kit: Function Flow Runtime Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @chuchihtung-->
<!--Designer: @zhanglu161-->
<!--Tester: @lotsof-->
<!--Adviser: @jinqiuheng-->

## 概述

声明[ffrt_usleep](capi-sleep-h.md#ffrt_usleep)和[ffrt_yield](capi-sleep-h.md#ffrt_yield)的C接口。

**引用文件：** <ffrt/sleep.h>

**库：** libffrt.z.so

**系统能力：** SystemCapability.Resourceschedule.Ffrt.Core

**起始版本：** 10

**相关模块：** [FFRT](capi-ffrt.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [FFRT_C_API int ffrt_usleep(uint64_t usec)](#ffrt_usleep) | 将调用线程挂起指定的时长。若`usec`超过支持的最大值则按最大值截断。 |
| [FFRT_C_API void ffrt_yield(void)](#ffrt_yield) | 将控制权让出给其他任务，使其有机会被执行。 |

## 函数说明

### ffrt_usleep()

```c
FFRT_C_API int ffrt_usleep(uint64_t usec)
```

**描述**

将调用线程挂起指定的时长。若`usec`超过支持的最大值则按最大值截断。

**起始版本：** 10

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t usec | 调用线程被挂起的时长，单位是微秒。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FFRT_C_API int | `ffrt_success`。该函数不会失败。 |

### ffrt_yield()

```c
FFRT_C_API void ffrt_yield(void)
```

**描述**

将控制权让出给其他任务，使其有机会被执行。

**起始版本：** 10


