# DateTimeRule

```c
typedef struct DateTimeRule {...} DateTimeRule
```

## Overview

Defines the date and time rules to specify a date and time.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t month | Indicates the month. The month starts from **0**, indicating January. |
| int32_t dayOfMonth | Indicates the day of a month. |
| int32_t dayOfWeek | Indicates the day of a week. |
| int32_t weekInMonth | Indicates the week in a month. |
| int32_t millisInDay | Indicates the millisecond value from 00:00 on the current day to the current time. |
| [DateRuleType](capi-timezone-h.md#dateruletype) dateRuleType | Indicates the date rule type. |
| [TimeRuleType](capi-timezone-h.md#timeruletype) timeRuleType | Indicates the time rule type. |


