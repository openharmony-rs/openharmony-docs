# TimeArrayTimeZoneRule

```c
typedef struct TimeArrayTimeZoneRule {...} TimeArrayTimeZoneRule
```

## Overview

Defines time zone rule defined by the start timestamp array.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* name | Indicates the name of the time zone rule. |
| int32_t rawOffset | Indicates the raw offset of the time zone, in milliseconds. |
| int32_t dstSavings | Indicates the daylight saving time offset, in milliseconds. |
| double* startTimes | Indicates the array of start timestamps when the rule takes effect. The timestamp unit is milliseconds. The caller is responsible for releasing the array. |
| int32_t numStartTimes | Indicates the size of the start timestamp array of the rule. |
| [TimeRuleType](capi-timezone-h.md#timeruletype) timeRuleType | Indicates the TimeRule of the rule to specify the time. |


