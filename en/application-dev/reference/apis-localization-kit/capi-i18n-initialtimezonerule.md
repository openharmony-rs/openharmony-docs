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
| int32_t rawOffset | Original offset of the time zone.|
| int32_t dstSavings | Offset of the daylight saving time.|
