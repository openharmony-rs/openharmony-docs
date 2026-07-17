# TriggerCondition

提供设置[Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md)的onTrigger回调触发条件的参数选项。

**起始版本：** 9

<!--Device-hiAppEvent-interface TriggerCondition--><!--Device-hiAppEvent-interface TriggerCondition-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## row

```TypeScript
row?: number
```

满足触发回调的事件总数量，正整数。默认值0，不触发回调。传入负值时，会被置为默认值。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerCondition-row?: int--><!--Device-TriggerCondition-row?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## size

```TypeScript
size?: number
```

满足触发回调的事件总大小，正整数，单位为byte。默认值0，不触发回调。传入负值时，会被置为默认值。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerCondition-size?: int--><!--Device-TriggerCondition-size?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## timeOut

```TypeScript
timeOut?: number
```

满足触发回调的超时时长，正整数，单位为s，值为timeOut * 30。默认值0，不触发回调。传入负值时，会被置为默认值。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TriggerCondition-timeOut?: int--><!--Device-TriggerCondition-timeOut?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

