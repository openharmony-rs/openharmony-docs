# TimeZoneRules

```c
typedef struct TimeZoneRules {...} TimeZoneRules
```

## Overview

A complete time zone rule includes the start time zone rule, time zone rule defined by the start timestamp array, and time zone rule that takes effect every year. It can comprehensively describe both the historical and future rules of a time zone.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

**Header file**: [timezone.h](capi-timezone-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [InitialTimeZoneRule](capi-i18n-initialtimezonerule.md) initial | Indicates the InitialTimeZoneRule of a timezone. |
| [TimeArrayTimeZoneRule*](capi-i18n-timearraytimezonerule.md) timeArrayRules | Indicates the TimeArrayTimeZoneRules of a timezone. The caller is responsible for releasing the array. |
| [AnnualTimeZoneRule*](capi-i18n-annualtimezonerule.md) annualRules | Indicates the AnnualTimeZoneRules of a timezone. The caller is responsible for releasing the array. |
| size_t numTimeArrayRules | Indicates the size of the time zone rule array defined by the start timestamp array. |
| size_t numAnnualRules | Indicates the size of the time zone rule array that takes effect annually. |


