# AppEventPackage

```TypeScript
interface AppEventPackage
```

Defines parameters of an **AppEventPackage** object. This API is used to obtain detail information about an event package, which is obtained using the [takeNext](arkts-performanceanalysis-hiappevent-appeventpackageholder-c.md#takenext) API.

**Since:** 9

<!--Device-hiAppEvent-interface AppEventPackage--><!--Device-hiAppEvent-interface AppEventPackage-End-->

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

**Atomic service API**: This parameter can be used in atomic services since API version 12.

**Type:** Array&lt;[AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md)&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AppEventPackage-appEventInfos: Array<AppEventInfo>--><!--Device-AppEventPackage-appEventInfos: Array<AppEventInfo>-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## data

```TypeScript
data: string[]
```

Event data in the event package.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** string[]

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AppEventPackage-data: string[]--><!--Device-AppEventPackage-data: string[]-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## packageId

```TypeScript
packageId: number
```

Event package ID, which is named from **0** in ascending order.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AppEventPackage-packageId: int--><!--Device-AppEventPackage-packageId: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## row

```TypeScript
row: number
```

Number of events in the event package.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AppEventPackage-row: int--><!--Device-AppEventPackage-row: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## size

```TypeScript
size: number
```

Event size of the event package, in bytes.

**Atomic service API**: This parameter can be used in atomic services since API version 11.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AppEventPackage-size: int--><!--Device-AppEventPackage-size: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
