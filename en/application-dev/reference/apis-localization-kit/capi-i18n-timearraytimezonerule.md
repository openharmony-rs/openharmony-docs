# TimeArrayTimeZoneRule

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=9da32f18d9f596600b1bcf7b3e4ed4f31b219c61 translatedAt=2026-11-09T06:18:51.731Z pushedAt=2026-11-09T06:56:17.246Z nl=1 -->

```c
typedef struct TimeArrayTimeZoneRule {...} TimeArrayTimeZoneRule
```

## Overview

Describes the time zone rule of the start timestamp array.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char* name | Name of the time zone rule.|
| int32_t rawOffset | Raw offset of the time zone, in milliseconds.|
| int32_t dstSavings | Daylight saving time offset, in milliseconds.|
| double* startTimes | Array of start timestamps when the rule takes effect. The timestamp unit is milliseconds.|
| int32_t numStartTimes | Size of the start timestamp array of the rule.|
| [TimeRuleType](capi-timezone-h.md#timeruletype) timeRuleType | Time rule type.|


