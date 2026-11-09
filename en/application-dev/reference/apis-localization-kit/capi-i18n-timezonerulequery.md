# TimeZoneRuleQuery

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=9da32f18d9f596600b1bcf7b3e4ed4f31b219c61 translatedAt=2026-11-09T06:18:54.187Z pushedAt=2026-11-09T06:56:59.529Z nl=1 -->

```c
typedef struct TimeZoneRuleQuery {...} TimeZoneRuleQuery
```

## Overview

Passes the query information and receives the query result.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| double base | Reference time for the query, in milliseconds. The value is Unix timestamp.|
| int32_t prevRawOffset | Previous raw offset of the time zone, in milliseconds.|
| int32_t prevDSTSavings | Previous daylight saving time offset, in milliseconds.|
| bool inclusive | Whether the query result contains the base time. The value **true** indicates that the query result contains the base time. The value **false** indicates the opposite.|
| double result | Query result, in milliseconds. The value is Unix timestamp.|


