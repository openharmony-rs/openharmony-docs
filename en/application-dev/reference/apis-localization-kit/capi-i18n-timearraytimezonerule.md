# TimeArrayTimeZoneRule

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

```c
typedef struct TimeArrayTimeZoneRule {...} TimeArrayTimeZoneRule
```

## Overview

Time zone rule defined by the start timestamp array.

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
