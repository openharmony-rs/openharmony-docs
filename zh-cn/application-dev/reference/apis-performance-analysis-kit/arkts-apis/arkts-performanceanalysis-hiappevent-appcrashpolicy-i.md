# AppCrashPolicy

提供崩溃事件配置策略的定义。

**起始版本：** 24

<!--Device-hiAppEvent-interface AppCrashPolicy--><!--Device-hiAppEvent-interface AppCrashPolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## collectMinidump

```TypeScript
collectMinidump?: boolean
```

APP_CRASH事件策略值为true表示启用日志转储捕获功能。false表示关闭日志转储功能。<br>默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AppCrashPolicy-collectMinidump?: boolean--><!--Device-AppCrashPolicy-collectMinidump?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## extendPcLrPrinting

```TypeScript
extendPcLrPrinting?: boolean
```

设置崩溃日志中是否打印pc和lr寄存器前后的内存值。

true：64位系统打印pc和lr寄存器地址向前248字节、向后256字节范围的内存值。32位系统打印pc和lr寄存器地址向前124字节、向后128字节范围的内存值。

false：64位系统打印pc和lr寄存器地址向前16字节、向后232字节范围的内存值。32位系统打印pc和lr寄存器地址向前8字节、向后116字节范围的内存值。

默认值：false。

26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AppCrashPolicy-extendPcLrPrinting?: boolean--><!--Device-AppCrashPolicy-extendPcLrPrinting?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## logFileCutoffSzBytes

```TypeScript
logFileCutoffSzBytes?: number
```

设置崩溃日志截断大小。单位为byte，取值范围为[0, 5242880]。默认值取0，表示不截断崩溃日志。

26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AppCrashPolicy-logFileCutoffSzBytes?: int--><!--Device-AppCrashPolicy-logFileCutoffSzBytes?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## pageSwitchLogEnable

```TypeScript
pageSwitchLogEnable?: boolean
```

是否使能崩溃事件的页面切换日志。

true：使能崩溃事件的页面切换日志。

false：不使能崩溃事件的页面切换日志。

默认值：false。

**说明**：应用每次使能行为只在应用当前生命周期生效，在同一生命周期内，以最后一次成功调用的使能状态为准。应用重启后，需要重新设置使能状态。

**类型：** boolean

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AppCrashPolicy-pageSwitchLogEnable?: boolean--><!--Device-AppCrashPolicy-pageSwitchLogEnable?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## simplifyVmaPrinting

```TypeScript
simplifyVmaPrinting?: boolean
```

设置崩溃日志是否打印所有VMA（Virtual Memory Area，虚拟内存空间）的映射信息，即崩溃日志中Maps。

true：只打印崩溃日志中出现的地址所属的VMA映射信息，以减小日志大小。

false：打印所有VMA映射信息。

默认值：false。

26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AppCrashPolicy-simplifyVmaPrinting?: boolean--><!--Device-AppCrashPolicy-simplifyVmaPrinting?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

