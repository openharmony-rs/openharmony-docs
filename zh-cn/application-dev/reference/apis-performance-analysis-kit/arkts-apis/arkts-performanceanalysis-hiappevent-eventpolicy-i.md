# EventPolicy

提供系统事件配置策略的定义，用于使用[configEventPolicy](arkts-performanceanalysis-hiappevent-configeventpolicy-f.md#configeventpolicy)设置事件配置策略。

**起始版本：** 22

<!--Device-hiAppEvent-interface EventPolicy--><!--Device-hiAppEvent-interface EventPolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## addressSanitizerPolicy

```TypeScript
addressSanitizerPolicy?: AddressSanitizerPolicy
```

地址越界事件配置策略。

**类型：** AddressSanitizerPolicy

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-EventPolicy-addressSanitizerPolicy?: AddressSanitizerPolicy--><!--Device-EventPolicy-addressSanitizerPolicy?: AddressSanitizerPolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## appCrashPolicy

```TypeScript
appCrashPolicy?: AppCrashPolicy
```

崩溃事件配置策略。

**类型：** AppCrashPolicy

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-EventPolicy-appCrashPolicy?: AppCrashPolicy--><!--Device-EventPolicy-appCrashPolicy?: AppCrashPolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## appFreezePolicy

```TypeScript
appFreezePolicy?: AppFreezePolicy
```

应用冻屏事件配置策略。

**类型：** AppFreezePolicy

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-EventPolicy-appFreezePolicy?: AppFreezePolicy--><!--Device-EventPolicy-appFreezePolicy?: AppFreezePolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## cpuUsageHighPolicy

```TypeScript
cpuUsageHighPolicy?: CpuUsageHighPolicy
```

CPU高负载事件配置策略。

**类型：** CpuUsageHighPolicy

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-EventPolicy-cpuUsageHighPolicy?: CpuUsageHighPolicy--><!--Device-EventPolicy-cpuUsageHighPolicy?: CpuUsageHighPolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## mainThreadJankPolicy

```TypeScript
mainThreadJankPolicy?: MainThreadJankPolicy
```

主线程超时事件配置策略。

**类型：** MainThreadJankPolicy

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-EventPolicy-mainThreadJankPolicy?: MainThreadJankPolicy--><!--Device-EventPolicy-mainThreadJankPolicy?: MainThreadJankPolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## resourceOverlimitPolicy

```TypeScript
resourceOverlimitPolicy?: ResourceOverlimitPolicy
```

资源泄漏事件配置策略。

**类型：** ResourceOverlimitPolicy

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-EventPolicy-resourceOverlimitPolicy?: ResourceOverlimitPolicy--><!--Device-EventPolicy-resourceOverlimitPolicy?: ResourceOverlimitPolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

