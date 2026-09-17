# AnnualTimeZoneRule

```c
typedef struct AnnualTimeZoneRule {...} AnnualTimeZoneRule
```

## Overview

Defines the time zone rule that takes effect annually.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* name | Indicates the name of the time zone rule. |
| int32_t startYear | Indicates the start year when the rule takes effective. |
| int32_t endYear | Indicates the end year when the rule takes effective. |
| int32_t rawOffset | Indicates the raw offset of the time zone, in milliseconds. |
| int32_t dstSavings | Indicates the daylight saving time offset, in milliseconds. |
| [DateTimeRule](capi-i18n-datetimerule.md) dateTimeRule | Indicates the rule of time and date. |


