# AppEventReportConfig

```TypeScript
interface AppEventReportConfig
```

Defines the event configuration for the data processor to report.

**Since:** 11

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## domain

```TypeScript
domain?: string
```

Event domain. The value is a string that contains a maximum of 32 characters, including digits (0 to 9), letters (a to z)(A to Z), and underscore (_). It must start with a letter and cannot end with an underscore (_). The default value is an empty string.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## isRealTime

```TypeScript
isRealTime?: boolean
```

Whether to report events in real time. The value **true** indicates that events are reported in real time, and the value **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## name

```TypeScript
name?: string
```

Event name. The value is string that contains a maximum of 48 characters, including digits (0 to 9), letters (a to z)(A to Z), underscore (_), and dollar sign ($). It must start with a letter or dollar sign ($) and end with a digit or letter. The default value is an empty string.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
