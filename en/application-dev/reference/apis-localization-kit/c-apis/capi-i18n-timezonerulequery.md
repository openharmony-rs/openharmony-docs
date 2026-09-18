# TimeZoneRuleQuery

```c
typedef struct TimeZoneRuleQuery {...} TimeZoneRuleQuery
```

## Overview

Used to input the query information and receive the query result.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| double base | Indicates the reference time for the query, in milliseconds. The value is Unix timestamp. |
| int32_t prevRawOffset | Indicates the previous raw offset of the time zone, in milliseconds. |
| int32_t prevDSTSavings | Indicates the previous daylight saving time offset, in milliseconds. |
| bool inclusive | Indicates whether the query result contains the base time. The value **true** indicates that the query result contains the base time. The value **false** indicates the opposite. |
| double result | Indicates the query result, in milliseconds. The value is Unix timestamp. |


