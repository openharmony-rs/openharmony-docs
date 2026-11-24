# DateTimeRule

```c
typedef struct DateTimeRule {...} DateTimeRule
```

## Overview

Defines the date and time rules to specify a date and time.

<!--Device-struct DateTimeRule {...}--><!--Device-struct DateTimeRule {...}-End-->

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Related module**: [i18n](capi-localization-kit-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t month | Indicates the month. The month starts from **0**, indicating January.<br><!--Device-int32_t month--><!--Device-int32_t month-End--> |
| int32_t dayOfMonth | Indicates the day of a month.<br><!--Device-int32_t dayOfMonth--><!--Device-int32_t dayOfMonth-End--> |
| int32_t dayOfWeek | Indicates the day of a week.<br><!--Device-int32_t dayOfWeek--><!--Device-int32_t dayOfWeek-End--> |
| int32_t weekInMonth | Indicates the week in a month.<br><!--Device-int32_t weekInMonth--><!--Device-int32_t weekInMonth-End--> |
| int32_t millisInDay | Indicates the millisecond value from 00:00 on the current day to the current time.<br><!--Device-int32_t millisInDay--><!--Device-int32_t millisInDay-End--> |
| [DateRuleType](capi-timezone-h.md#dateruletype) dateRuleType | Indicates the date rule type.<br><!--Device-DateRuleType dateRuleType--><!--Device-DateRuleType dateRuleType-End--> |
| [TimeRuleType](capi-timezone-h.md#timeruletype) timeRuleType | Indicates the time rule type.<br><!--Device-TimeRuleType timeRuleType--><!--Device-TimeRuleType timeRuleType-End--> |


