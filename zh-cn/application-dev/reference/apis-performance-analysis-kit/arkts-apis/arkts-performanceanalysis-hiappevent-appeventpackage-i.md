# AppEventPackage

提供订阅返回的事件包的参数定义。可用于获取事件包的详细信息，事件包由[takeNext](arkts-performanceanalysis-hiappevent-appeventpackageholder-c.md#takenext-1)接口获得。

**起始版本：** 9

<!--Device-hiAppEvent-interface AppEventPackage--><!--Device-hiAppEvent-interface AppEventPackage-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## appEventInfos

```TypeScript
appEventInfos: Array<AppEventInfo>
```

事件对象集合。

**原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。

**类型：** Array&lt;AppEventInfo&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventPackage-appEventInfos: Array<AppEventInfo>--><!--Device-AppEventPackage-appEventInfos: Array<AppEventInfo>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## data

```TypeScript
data: string[]
```

事件包的事件信息。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** string[]

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventPackage-data: string[]--><!--Device-AppEventPackage-data: string[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## packageId

```TypeScript
packageId: number
```

事件包ID，从0开始自动递增。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventPackage-packageId: int--><!--Device-AppEventPackage-packageId: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## row

```TypeScript
row: number
```

事件包的事件数量。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventPackage-row: int--><!--Device-AppEventPackage-row: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## size

```TypeScript
size: number
```

事件包的事件大小，单位为byte。

**原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventPackage-size: int--><!--Device-AppEventPackage-size: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

