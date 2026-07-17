# MainThreadJankPolicy

提供主线程超时事件配置策略的定义。

**起始版本：** 22

<!--Device-hiAppEvent-interface MainThreadJankPolicy--><!--Device-hiAppEvent-interface MainThreadJankPolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## autoStopSampling

```TypeScript
autoStopSampling?: boolean
```

主线程超时结束时，是否自动停止采样主线程堆栈。

true: 超时结束或达到设置的采样次数，停止采样。

false：达到设置的采样次数时停止采样。

默认值：false。

**类型：** boolean

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-MainThreadJankPolicy-autoStopSampling?: boolean--><!--Device-MainThreadJankPolicy-autoStopSampling?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## ignoreStartupTime

```TypeScript
ignoreStartupTime?: number
```

应用启动期间忽略主线程超时检测的时间。单位：秒，默认值：10，最小值：3。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-MainThreadJankPolicy-ignoreStartupTime?: int--><!--Device-MainThreadJankPolicy-ignoreStartupTime?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## logType

```TypeScript
logType?: number
```

采集日志的类型。默认值：0。

logType=0：其他选项均取默认值，主线程连续两次超时150ms~450ms，采集调用栈；主线程超时450ms，采集trace。

logType=1：仅采集调用栈，触发检测的阈值由用户自定义。

logType=2：仅采集trace。

**说明**：

- logType=0时，仅需配置autoStopSampling参数，其他参数均取默认值，无需设置。  
- logType=2时，其他参数均不生效，无需设置。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-MainThreadJankPolicy-logType?: int--><!--Device-MainThreadJankPolicy-logType?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## reportTimesPerApp

```TypeScript
reportTimesPerApp?: number
```

同一个应用的PID一个生命周期内，主线程超时采样上报次数。一个生命周期内只能设置一次。

默认值：1，单位：次。

每分钟上报次数范围：[1, 3]。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-MainThreadJankPolicy-reportTimesPerApp?: int--><!--Device-MainThreadJankPolicy-reportTimesPerApp?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## sampleCount

```TypeScript
sampleCount?: number
```

主线程超时采样次数。单位：次，默认值：10，最小值：1。

最大值需要结合自定义的sampleInterval进行动态计算，计算公式：sampleCount <= (2500 / sampleInterval - 4)。

**说明**：

- 2500的含义：根据系统规定，主线程超时事件从检测到上报的时间不可以超过2.5s（即：2500ms）。因此sampleCount的设置值不能超过系统按计算公式得出的最大值。  
- 4的含义：第一次超时间隔检测时间 + 第二次超时间隔（系统提供两次再次发生超时事件的检测机会）时间 + 收集并上报堆栈信息的时间。  
- 开发者要结合需求场景，进行合理的设置。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-MainThreadJankPolicy-sampleCount?: int--><!--Device-MainThreadJankPolicy-sampleCount?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## sampleInterval

```TypeScript
sampleInterval?: number
```

主线程超时检测间隔和采样间隔。单位：毫秒，默认值：150，取值范围：[50, 500]。

**类型：** number

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-MainThreadJankPolicy-sampleInterval?: int--><!--Device-MainThreadJankPolicy-sampleInterval?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

