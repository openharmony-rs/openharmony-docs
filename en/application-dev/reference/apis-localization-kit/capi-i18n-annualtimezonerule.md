# AnnualTimeZoneRule

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=9da32f18d9f596600b1bcf7b3e4ed4f31b219c61 translatedAt=2026-11-09T06:18:39.174Z pushedAt=2026-11-09T06:55:13.728Z nl=1 -->

```c
typedef struct AnnualTimeZoneRule {...} AnnualTimeZoneRule
```

## Overview

Describes the time zone rule that takes effect annually.

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
| int32_t rawOffset | Raw offset of the time zone, in milliseconds.|
| int32_t dstSavings | Daylight saving time offset, in milliseconds.|
| [DateTimeRule](capi-i18n-datetimerule.md) dateTimeRule | Rule of time and date.|


