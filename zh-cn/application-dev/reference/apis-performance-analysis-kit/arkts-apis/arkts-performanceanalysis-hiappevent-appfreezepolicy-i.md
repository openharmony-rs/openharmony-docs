# AppFreezePolicy

提供应用冻屏事件配置策略的定义。

**起始版本：** 24

<!--Device-hiAppEvent-interface AppFreezePolicy--><!--Device-hiAppEvent-interface AppFreezePolicy-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## pageSwitchLogEnable

```TypeScript
pageSwitchLogEnable?: boolean
```

是否使能应用冻屏事件的页面切换日志。

true：使能应用冻屏事件的页面切换日志。

false：不使能应用冻屏事件的页面切换日志。

默认值：false。

**说明**：应用每次使能行为只在应用当前生命周期生效，在同一生命周期内，以最后一次成功调用的使能状态为准。应用重启后，需要重新设置使能状态。

**类型：** boolean

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AppFreezePolicy-pageSwitchLogEnable?: boolean--><!--Device-AppFreezePolicy-pageSwitchLogEnable?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

