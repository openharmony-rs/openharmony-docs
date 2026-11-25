# InitialTimeZoneRule

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=dd15b2c3bd81ae9fa6656096d98554e6b206e3bc translatedAt=2026-11-04T03:47:44.675Z pushedAt=2026-11-04T10:13:14.871Z nl=1 -->

```c
typedef struct InitialTimeZoneRule {...} InitialTimeZoneRule
```

## Overview

Start time zone rule.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t rawOffset | Raw offset of the time zone, in milliseconds. |
| int32_t dstSavings | Daylight saving time offset, in milliseconds. |


