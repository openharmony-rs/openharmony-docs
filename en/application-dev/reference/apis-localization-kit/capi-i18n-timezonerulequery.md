# TimeZoneRuleQuery

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

```c
typedef struct TimeZoneRuleQuery {...} TimeZoneRuleQuery
```

## Overview

Used to input the query information and receive the query result.

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| double base | Base time of the query.|
| int32_t prevRawOffset | Original offset of the time zone last time.|
| int32_t prevDSTSavings | Original DST offset last time.|
| bool inclusive | Whether the query result contains the base time. The value **true** indicates that the query result contains the base time. The value **false** indicates the opposite.|
| double result | Query result.|
