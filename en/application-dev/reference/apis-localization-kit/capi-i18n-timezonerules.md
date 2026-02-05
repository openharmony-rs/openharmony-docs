# TimeZoneRules

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

```c
typedef struct TimeZoneRules {...} TimeZoneRules
```

## Overview

Complete time zone rule.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [InitialTimeZoneRule](capi-i18n-initialtimezonerule.md) initial | Start time zone rule.|
| [TimeArrayTimeZoneRule*](capi-i18n-timearraytimezonerule.md) timeArrayRules | Time zone rule array defined by the start timestamp array.|
| [AnnualTimeZoneRule*](capi-i18n-annualtimezonerule.md) annualRules | Time zone rule array that takes effect annually.|
| size_t numTimeArrayRules | Size of the time zone rule array defined by the start timestamp array.|
| size_t numAnnualRules | Size of the time zone rule array that takes effect annually.|
