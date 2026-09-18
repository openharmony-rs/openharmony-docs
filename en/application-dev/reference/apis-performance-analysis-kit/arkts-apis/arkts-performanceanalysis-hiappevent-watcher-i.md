# Watcher

Defines parameters for a **Watcher** object. This API is used to configure and manage event watchers to subscribe to and process specified events.

> **NOTE:** 
> 
> You are not advised to call [removeWatcher](arkts-performanceanalysis-hiappevent-removewatcher-f.md) in the callback. Once a watcher is
> removed, the subscription callback of the watcher becomes invalid, and the callback may not be triggered when an
> event occurs.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## onReceive

```TypeScript
onReceive?: (domain: string, appEventGroups: Array<AppEventGroup>) => void
```

Real-time subscription callback. Only this callback function is triggered if it is passed together with **onTrigger**. The input arguments are described as follows:

domain: domain name.

appEventGroups: event group.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domain | string | Yes |  |
| appEventGroups | Array&lt;[AppEventGroup](arkts-performanceanalysis-hiappevent-appeventgroup-i.md)&gt; | Yes |  |

## onTrigger

```TypeScript
onTrigger?: (curRow: number, curSize: number, holder: AppEventPackageHolder) => void
```

Subscription callback. This parameter takes effect only when it is passed together with **triggerCondition**. The input arguments are described as follows:

**curRow**: total number of subscription events when the callback is triggered.

**curSize**: total size of subscribed events when the callback is triggered, in bytes.

**holder**: subscription data holder, which can be used to process subscribed events.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| curRow | number | Yes |  |
| curSize | number | Yes |  |
| holder | [AppEventPackageHolder](arkts-performanceanalysis-hiappevent-appeventpackageholder-c.md) | Yes |  |

## appEventFilters

```TypeScript
appEventFilters?: AppEventFilter[]
```

Subscription filtering condition. This parameter is passed only when subscription events need to be filtered. If this parameter is not set, events are not filtered by default.

**Type:** [AppEventFilter](arkts-performanceanalysis-hiappevent-appeventfilter-i.md)[]

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## name

```TypeScript
name: string
```

Unique name of a watcher. The value contains a maximum of 32 characters, including digits (0 to 9), letters (a to z)(A to Z), and underscore (_). It must start with a letter and end with a digit or letter. For example, **testName1** and **crash_Watcher**.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## triggerCondition

```TypeScript
triggerCondition?: TriggerCondition
```

Subscription callback triggering condition. This parameter takes effect only when it is passed together with **onTrigger**. If this parameter is not set, the **onTrigger** callback is not triggered by default.

**Type:** [TriggerCondition](arkts-performanceanalysis-hiappevent-triggercondition-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
