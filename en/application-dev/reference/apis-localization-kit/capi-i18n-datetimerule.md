# DateTimeRule

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

```c
typedef struct DateTimeRule {...} DateTimeRule
```

## Overview

Rule of time and date.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t month | Month.|
| int32_t dayOfMonth | Day of the month.|
| int32_t dayOfWeek | Day of the week.|
| int32_t weekInMonth | Week of the month.|
| int32_t millisInDay | Millisecond value from 00:00 on the current day to the current time.|
| [DateRuleType](capi-timezone-h.md#dateruletype) dateRuleType | Date rule type.|
| [TimeRuleType](capi-timezone-h.md#timeruletype) timeRuleType | Time rule type.|
