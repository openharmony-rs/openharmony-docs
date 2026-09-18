# InitialTimeZoneRule

```c
typedef struct InitialTimeZoneRule {...} InitialTimeZoneRule
```

## Overview

Defines the initial rule of a timezone which has no clear start time.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t rawOffset | Indicates the raw offset of the time zone, in milliseconds. |
| int32_t dstSavings | Indicates the daylight saving time offset, in milliseconds. |


