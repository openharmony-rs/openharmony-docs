# InitialTimeZoneRule

```c
typedef struct InitialTimeZoneRule {...} InitialTimeZoneRule
```

## Overview

Defines the initial rule of a timezone which has no clear start time.

<!--Device-struct InitialTimeZoneRule {...}--><!--Device-struct InitialTimeZoneRule {...}-End-->

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Related module**: [i18n](capi-localization-kit-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t rawOffset | Indicates the raw offset of the time zone, in milliseconds.<br><!--Device-int32_t rawOffset--><!--Device-int32_t rawOffset-End--> |
| int32_t dstSavings | Indicates the daylight saving time offset, in milliseconds.<br><!--Device-int32_t dstSavings--><!--Device-int32_t dstSavings-End--> |


