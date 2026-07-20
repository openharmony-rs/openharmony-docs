# AppEventGroup

提供订阅返回的事件组的参数定义。可用于获取事件组的详细信息，事件组常在[Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md)的onReceive回调中使用。

**起始版本：** 11

<!--Device-hiAppEvent-interface AppEventGroup--><!--Device-hiAppEvent-interface AppEventGroup-End-->

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

**类型：** Array&lt;AppEventInfo&gt;

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventGroup-appEventInfos: Array<AppEventInfo>--><!--Device-AppEventGroup-appEventInfos: Array<AppEventInfo>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## name

```TypeScript
name: string
```

事件名称。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventGroup-name: string--><!--Device-AppEventGroup-name: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

