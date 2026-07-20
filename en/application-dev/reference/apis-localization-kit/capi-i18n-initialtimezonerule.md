# InitialTimeZoneRule

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

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
| int32_t rawOffset | Raw offset of the time zone, in milliseconds.|
| int32_t dstSavings | Daylight saving time offset, in milliseconds.|
