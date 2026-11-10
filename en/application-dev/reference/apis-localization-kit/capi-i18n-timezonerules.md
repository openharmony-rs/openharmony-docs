# TimeZoneRules

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=9da32f18d9f596600b1bcf7b3e4ed4f31b219c61 translatedAt=2026-11-09T06:19:07.869Z pushedAt=2026-11-09T06:57:35.753Z nl=1 -->

```c
typedef struct TimeZoneRules {...} TimeZoneRules
```

## Overview

Describes the complete time zone rules, including the start time zone rule, time zone rule of the start timestamp array, and time zone rule that takes effect every year. It can comprehensively describe both the historical and future rules of a time zone.

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


