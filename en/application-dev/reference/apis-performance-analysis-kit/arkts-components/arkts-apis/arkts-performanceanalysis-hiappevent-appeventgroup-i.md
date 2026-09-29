# AppEventGroup

```TypeScript
interface AppEventGroup
```

Defines parameters of the event group returned by the subscription. This API can be used to obtain detail information about an event group, which is often used in the **onReceive** callback of [Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md).

**Since:** 11

<!--Device-hiAppEvent-interface AppEventGroup--><!--Device-hiAppEvent-interface AppEventGroup-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## appEventInfos

```TypeScript
appEventInfos: Array<AppEventInfo>
```

Event object group.

**Type:** Array&lt;[AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md)&gt;

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AppEventGroup-appEventInfos: Array<AppEventInfo>--><!--Device-AppEventGroup-appEventInfos: Array<AppEventInfo>-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## name

```TypeScript
name: string
```

Event name.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AppEventGroup-name: string--><!--Device-AppEventGroup-name: string-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
