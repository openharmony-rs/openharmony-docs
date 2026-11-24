# AnnualTimeZoneRule

```c
typedef struct AnnualTimeZoneRule {...} AnnualTimeZoneRule
```

## Overview

Defines the time zone rule that takes effect annually.

<!--Device-struct AnnualTimeZoneRule {...}--><!--Device-struct AnnualTimeZoneRule {...}-End-->

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Related module**: [i18n](capi-localization-kit-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* name | Indicates the name of the time zone rule.<br><!--Device-char* name--><!--Device-char* name-End--> |
| int32_t startYear | Indicates the start year when the rule takes effective.<br><!--Device-int32_t startYear--><!--Device-int32_t startYear-End--> |
| int32_t endYear | Indicates the end year when the rule takes effective.<br><!--Device-int32_t endYear--><!--Device-int32_t endYear-End--> |
| int32_t rawOffset | Indicates the raw offset of the time zone, in milliseconds.<br><!--Device-int32_t rawOffset--><!--Device-int32_t rawOffset-End--> |
| int32_t dstSavings | Indicates the daylight saving time offset, in milliseconds.<br><!--Device-int32_t dstSavings--><!--Device-int32_t dstSavings-End--> |
| [DateTimeRule](capi-i18n-datetimerule.md) dateTimeRule | Indicates the rule of time and date.<br><!--Device-DateTimeRule dateTimeRule--><!--Device-DateTimeRule dateTimeRule-End--> |


