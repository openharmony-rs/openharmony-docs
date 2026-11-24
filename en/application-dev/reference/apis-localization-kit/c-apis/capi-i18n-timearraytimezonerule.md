# TimeArrayTimeZoneRule

```c
typedef struct TimeArrayTimeZoneRule {...} TimeArrayTimeZoneRule
```

## Overview

Defines time zone rule defined by the start timestamp array.

<!--Device-struct TimeArrayTimeZoneRule {...}--><!--Device-struct TimeArrayTimeZoneRule {...}-End-->

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Related module**: [i18n](capi-localization-kit-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* name | Indicates the name of the time zone rule.<br><!--Device-char* name--><!--Device-char* name-End--> |
| int32_t rawOffset | Indicates the raw offset of the time zone, in milliseconds.<br><!--Device-int32_t rawOffset--><!--Device-int32_t rawOffset-End--> |
| int32_t dstSavings | Indicates the daylight saving time offset, in milliseconds.<br><!--Device-int32_t dstSavings--><!--Device-int32_t dstSavings-End--> |
| double* startTimes | Indicates the array of start timestamps when the rule takes effect. The timestamp unit is milliseconds. The caller is responsible for releasing the array.<br><!--Device-double* startTimes--><!--Device-double* startTimes-End--> |
| int32_t numStartTimes | Indicates the size of the start timestamp array of the rule.<br><!--Device-int32_t numStartTimes--><!--Device-int32_t numStartTimes-End--> |
| [TimeRuleType](capi-timezone-h.md#timeruletype) timeRuleType | Indicates the TimeRule of the rule to specify the time.<br><!--Device-TimeRuleType timeRuleType--><!--Device-TimeRuleType timeRuleType-End--> |


