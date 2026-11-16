# AnnualTimeZoneRule

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=1a7fdda7cb0bdacc6b1c367c8fd0def17530cd88 translatedAt=2026-11-04T03:47:29.347Z pushedAt=2026-11-04T10:13:14.867Z nl=1 -->

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
| int32_t rawOffset | Raw offset of the time zone, in milliseconds. |
| int32_t dstSavings | Daylight saving time offset, in milliseconds. |
| [DateTimeRule](capi-i18n-datetimerule.md) dateTimeRule | Rule of time and date.|


