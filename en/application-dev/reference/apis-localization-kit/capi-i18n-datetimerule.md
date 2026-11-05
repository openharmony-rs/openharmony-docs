# DateTimeRule

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=1a7fdda7cb0bdacc6b1c367c8fd0def17530cd88 translatedAt=2026-11-04T03:47:40.400Z pushedAt=2026-11-04T10:13:14.869Z nl=1 -->

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
| int32_t month | Month. The month starts from **0**, indicating January. |
| int32_t dayOfMonth | Day of the month.|
| int32_t dayOfWeek | Day of the week.|
| int32_t weekInMonth | Week of the month.|
| int32_t millisInDay | Millisecond value from 00:00 on the current day to the current time.|
| [DateRuleType](capi-timezone-h.md#dateruletype) dateRuleType | Date rule type.|
| [TimeRuleType](capi-timezone-h.md#timeruletype) timeRuleType | Time rule type.|


