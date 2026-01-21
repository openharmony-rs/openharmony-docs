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
| int32_t rawOffset | Original offset of the time zone.|
| int32_t dstSavings | Offset of the daylight saving time.|
| double* startTimes | Start timestamp array of the rule.|
| int32_t numStartTimes | Size of the start timestamp array of the rule.|
| [TimeRuleType](capi-timezone-h.md#timeruletype) timeRuleType | Time rule type.|
