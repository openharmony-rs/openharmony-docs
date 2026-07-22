# PerfMetric

框架支持采集的性能指标。
> **说明**  
>  
>  
> - 测试过程中，代码段执行开始前和代码段执行结束后，会分别采集指定应用进程的CPU和内存数据，因此测试过程中需要保证被测应用进程一直存在。  
>  
>  
> - 应用启动时延数据受系统打点上报限制，开始时间为点击事件上报时间点，响应时延结束时间为点击后系统响应首帧的上屏时间点（首帧显示在屏幕上的时间点），完成时延结束时间为应用启动后的首帧上屏时间点，与端到端用户感知时延存在差异。  
>  
> - 应用启动时延数据采集支持的场景：桌面点击应用图标启动、Dock栏点击应用图标启动、应用中心点击应用图标启动。  
>  
> - 单次测试期间，仅第一次指定应用启动的时延数据会被采集。  
>  
>  
> - 页面切换时延计算受系统打点上报限制，开始时间为点击事件上报时间点，完成时延结束时间为页面切换后的首帧上屏时间点，与端到端用户感知时延存在差异。  
>  
> - 页面切换时延数据采集支持的场景：Router、Navigation控件内的页面切换。  
>  
> - 单次测试期间，仅指定应用内第一次页面切换的时延数据会被采集。  
>  
>  
> - 列表滑动帧率：指的是在列表滑动时，屏幕每秒钟渲染更新帧的次数。  
>  
> - 列表滑动帧率数据采集支持的场景：ArkUI子系统List、Grid、scroll、waterflow滚动控件列表的滑动。  
>  
> - 单次测试期间，仅指定应用内第一次列表滑动的帧率数据会被采集。

**起始版本：** 20

<!--Device-unnamed-declare enum PerfMetric--><!--Device-unnamed-declare enum PerfMetric-End-->

**系统能力：** SystemCapability.Test.PerfTest

## DURATION

```TypeScript
DURATION = 0
```

代码段执行耗时，单位：ms。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMetric-DURATION = 0--><!--Device-PerfMetric-DURATION = 0-End-->

**系统能力：** SystemCapability.Test.PerfTest

## CPU_LOAD

```TypeScript
CPU_LOAD = 1
```

应用进程CPU负载，取值为百分比。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMetric-CPU_LOAD = 1--><!--Device-PerfMetric-CPU_LOAD = 1-End-->

**系统能力：** SystemCapability.Test.PerfTest

## CPU_USAGE

```TypeScript
CPU_USAGE = 2
```

应用进程CPU使用率，取值为百分比。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMetric-CPU_USAGE = 2--><!--Device-PerfMetric-CPU_USAGE = 2-End-->

**系统能力：** SystemCapability.Test.PerfTest

## MEMORY_RSS

```TypeScript
MEMORY_RSS = 3
```

代码段单次执行结束时，应用进程占用物理内存（含共享库），单位：KB。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMetric-MEMORY_RSS = 3--><!--Device-PerfMetric-MEMORY_RSS = 3-End-->

**系统能力：** SystemCapability.Test.PerfTest

## MEMORY_PSS

```TypeScript
MEMORY_PSS = 4
```

代码段单次执行结束时，应用进程占用物理内存（不含共享库），单位：KB。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMetric-MEMORY_PSS = 4--><!--Device-PerfMetric-MEMORY_PSS = 4-End-->

**系统能力：** SystemCapability.Test.PerfTest

## APP_START_RESPONSE_TIME

```TypeScript
APP_START_RESPONSE_TIME = 5
```

应用启动的响应时延，单位：ms。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMetric-APP_START_RESPONSE_TIME = 5--><!--Device-PerfMetric-APP_START_RESPONSE_TIME = 5-End-->

**系统能力：** SystemCapability.Test.PerfTest

## APP_START_COMPLETE_TIME

```TypeScript
APP_START_COMPLETE_TIME = 6
```

应用启动的完成时延，单位：ms。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMetric-APP_START_COMPLETE_TIME = 6--><!--Device-PerfMetric-APP_START_COMPLETE_TIME = 6-End-->

**系统能力：** SystemCapability.Test.PerfTest

## PAGE_SWITCH_COMPLETE_TIME

```TypeScript
PAGE_SWITCH_COMPLETE_TIME = 7
```

应用内页面切换的完成时延，单位：ms。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMetric-PAGE_SWITCH_COMPLETE_TIME = 7--><!--Device-PerfMetric-PAGE_SWITCH_COMPLETE_TIME = 7-End-->

**系统能力：** SystemCapability.Test.PerfTest

## LIST_SWIPE_FPS

```TypeScript
LIST_SWIPE_FPS = 8
```

应用内列表滑动的帧率，单位：fps。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMetric-LIST_SWIPE_FPS = 8--><!--Device-PerfMetric-LIST_SWIPE_FPS = 8-End-->

**系统能力：** SystemCapability.Test.PerfTest

