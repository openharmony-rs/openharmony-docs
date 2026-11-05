# TimeZoneRules

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=1a7fdda7cb0bdacc6b1c367c8fd0def17530cd88 translatedAt=2026-11-04T03:48:17.662Z pushedAt=2026-11-04T10:13:14.876Z nl=1 -->

```c
typedef struct TimeZoneRules {...} TimeZoneRules
```

## Overview

A complete time zone rule includes the start time zone rule, time zone rule defined by the start timestamp array, and time zone rule that takes effect every year. It can comprehensively describe both the historical and future rules of a time zone.

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


