# EventPolicy

提供系统事件配置策略的定义，用于使用[configEventPolicy](arkts-performanceanalysis-hiappevent-configeventpolicy-f.md)设置事件配置策略。

**起始版本：** 22

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
```

## addressSanitizerPolicy

```TypeScript
addressSanitizerPolicy?: AddressSanitizerPolicy
```

地址越界事件配置策略。

**类型：** [AddressSanitizerPolicy](arkts-performanceanalysis-hiappevent-addresssanitizerpolicy-i.md)

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## appCrashPolicy

```TypeScript
appCrashPolicy?: AppCrashPolicy
```

崩溃事件配置策略。

**类型：** [AppCrashPolicy](arkts-performanceanalysis-hiappevent-appcrashpolicy-i.md)

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## appFreezePolicy

```TypeScript
appFreezePolicy?: AppFreezePolicy
```

应用冻屏事件配置策略。

**类型：** [AppFreezePolicy](arkts-performanceanalysis-hiappevent-appfreezepolicy-i.md)

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## cpuUsageHighPolicy

```TypeScript
cpuUsageHighPolicy?: CpuUsageHighPolicy
```

CPU高负载事件配置策略。

**类型：** [CpuUsageHighPolicy](arkts-performanceanalysis-hiappevent-cpuusagehighpolicy-i.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## mainThreadJankPolicy

```TypeScript
mainThreadJankPolicy?: MainThreadJankPolicy
```

主线程超时事件配置策略。

**类型：** [MainThreadJankPolicy](arkts-performanceanalysis-hiappevent-mainthreadjankpolicy-i.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## resourceOverlimitPolicy

```TypeScript
resourceOverlimitPolicy?: ResourceOverlimitPolicy
```

资源泄漏事件配置策略。

**类型：** [ResourceOverlimitPolicy](arkts-performanceanalysis-hiappevent-resourceoverlimitpolicy-i.md)

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent
