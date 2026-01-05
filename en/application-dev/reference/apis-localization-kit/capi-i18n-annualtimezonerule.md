# AnnualTimeZoneRule

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

```c
typedef struct AnnualTimeZoneRule {...} AnnualTimeZoneRule
```

## Overview

Time zone rule that takes effect annually.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char* name | Name of the time zone rule.|
| int32_t startYear | Start year when the time zone rule takes effect.|
| int32_t endYear | End year when the time zone rule takes effect.|
| int32_t rawOffset | Original offset of the time zone.|
| int32_t dstSavings | Offset of the daylight saving time.|
| [DateTimeRule](capi-i18n-datetimerule.md) dateTimeRule | Rule of time and date.|
