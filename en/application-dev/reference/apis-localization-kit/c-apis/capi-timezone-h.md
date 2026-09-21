# timezone.h

## Overview

Provides the capability of obtaining time zone information.

**Library**: libohi18n.so

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Related module**: [i18n](capi-i18n.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [DateTimeRule](capi-i18n-datetimerule.md) | DateTimeRule | Defines the date and time rules to specify a date and time. |
| [InitialTimeZoneRule](capi-i18n-initialtimezonerule.md) | InitialTimeZoneRule | Defines the initial rule of a timezone which has no clear start time. |
| [TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md) | TimeArrayTimeZoneRule | Defines time zone rule defined by the start timestamp array. |
| [AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md) | AnnualTimeZoneRule | Defines the time zone rule that takes effect annually. |
| [TimeZoneRules](capi-i18n-timezonerules.md) | TimeZoneRules | A complete time zone rule includes the start time zone rule, time zone rule defined by the start timestamp array, and time zone rule that takes effect every year. It can comprehensively describe both the historical and future rules of a time zone. |
| [TimeZoneRuleQuery](capi-i18n-timezonerulequery.md) | TimeZoneRuleQuery | Used to input the query information and receive the query result. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [DateRuleType](#dateruletype) | DateRuleType | Enumerates the types of rules for defining dates. |
| [TimeRuleType](#timeruletype) | TimeRuleType | Enumerates the types of rules for defining time. |

### Macro

| Name | Description |
| -- | -- |
| MAX_YEAR_IN_ANNUAL_TIMEZONE_RULE 0x7fffffff | Indicates the maximum year when the rule takes effective in AnnualTimeZoneRule.<br>**Since**: 22 |

### Function

| Name | Description |
| -- | -- |
| [I18n_ErrorCode OH_i18n_GetTimeZoneRules(const char* timeZoneID, TimeZoneRules* rules)](#oh_i18n_gettimezonerules) | Obtains the timezone rules by timezone ID. |
| [I18n_ErrorCode OH_i18n_GetFirstStartFromTimeArrayTimeZoneRule(TimeArrayTimeZoneRule* rule, TimeZoneRuleQuery* query)](#oh_i18n_getfirststartfromtimearraytimezonerule) | Obtains the time when the TimeArrayTimeZoneRule first took effect. |
| [I18n_ErrorCode OH_i18n_GetFirstStartFromAnnualTimeZoneRule(AnnualTimeZoneRule* rule, TimeZoneRuleQuery* query)](#oh_i18n_getfirststartfromannualtimezonerule) | Obtains the time when the AnnualTimeZoneRule first took effect. |
| [I18n_ErrorCode OH_i18n_GetFinalStartFromTimeArrayTimeZoneRule(TimeArrayTimeZoneRule* rule, TimeZoneRuleQuery* query)](#oh_i18n_getfinalstartfromtimearraytimezonerule) | Obtains the time when the TimeArrayTimeZoneRule final took effect. |
| [I18n_ErrorCode OH_i18n_GetFinalStartFromAnnualTimeZoneRule(AnnualTimeZoneRule* rule, TimeZoneRuleQuery* query)](#oh_i18n_getfinalstartfromannualtimezonerule) | Obtains the time when the AnnualTimeZoneRule final took effect. |
| [I18n_ErrorCode OH_i18n_GetNextStartFromTimeArrayTimeZoneRule(TimeArrayTimeZoneRule* rule, TimeZoneRuleQuery* query)](#oh_i18n_getnextstartfromtimearraytimezonerule) | Obtains the time when the TimeArrayTimeZoneRule next took effect. |
| [I18n_ErrorCode OH_i18n_GetNextStartFromAnnualTimeZoneRule(AnnualTimeZoneRule* rule, TimeZoneRuleQuery* query)](#oh_i18n_getnextstartfromannualtimezonerule) | Obtains the time when the AnnualTimeZoneRule next took effect. |
| [I18n_ErrorCode OH_i18n_GetPrevStartFromTimeArrayTimeZoneRule(TimeArrayTimeZoneRule* rule, TimeZoneRuleQuery* query)](#oh_i18n_getprevstartfromtimearraytimezonerule) | Obtains the time when the TimeArrayTimeZoneRule previous took effect. |
| [I18n_ErrorCode OH_i18n_GetPrevStartFromAnnualTimeZoneRule(AnnualTimeZoneRule* rule, TimeZoneRuleQuery* query)](#oh_i18n_getprevstartfromannualtimezonerule) | Obtains the time when the AnnualTimeZoneRule previous took effect. |
| [I18n_ErrorCode OH_i18n_GetStartTimeAt(TimeArrayTimeZoneRule* rule, int32_t index, double* result)](#oh_i18n_getstarttimeat) | Obtain the effective start time of a specific rule in the TimeArrayTimeZoneRule. |
| [I18n_ErrorCode OH_i18n_GetStartInYear(AnnualTimeZoneRule* rule, int32_t year, TimeZoneRuleQuery* query)](#oh_i18n_getstartinyear) | Obtain the effective start time of a specific rule for target year in the AnnualTimeZoneRule. |

## Enum type description

### DateRuleType

```c
enum DateRuleType
```

**Description**

Enumerates the types of rules for defining dates.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

| Enum item | Description |
| -- | -- |
| DOM = 0 | Indicates that day of the month. For example, October 16 in 2025 is the 16th day of October. |
| DOW = 1 | Indicates that weekday of the month. For example, October 16 in 2025 is the third Thursday of October. |
| DOW_GEQ_DOM = 2 | Indicates that first weekday after the specified day of the month. For example, October 16 in 2025 is the first Thursday after the 13th, 14th, or 15th day of October. |
| DOW_LEQ_DOM = 3 | Indicates that last weekday before the specified day of the month. For example, October 16 in 2025 is the last Thursday before the 20th day of October. |

### TimeRuleType

```c
enum TimeRuleType
```

**Description**

Enumerates the types of rules for defining time.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

| Enum item | Description |
| -- | -- |
| WALL_TIME = 0 | Indicates that local clock time (not subject to time zone offset). |
| STANDARD_TIME = 1 | Indicates that local standard time (not subject to DST offset). |
| UTC_TIME = 2 | Indicates that world standard time (UTC time). |


## Function description

### OH_i18n_GetTimeZoneRules()

```c
I18n_ErrorCode OH_i18n_GetTimeZoneRules(const char* timeZoneID, TimeZoneRules* rules)
```

**Description**

Obtains the timezone rules by timezone ID.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* timeZoneID | Indicates the timezone ID, such as **Asia/Shanghai**. |
| [TimeZoneRules](capi-i18n-timezonerules.md)* rules | Indicates the TimeZoneRules[TimeZoneRules](capi-i18n-timezonerules.md) of timezoneID. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes: Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |

### OH_i18n_GetFirstStartFromTimeArrayTimeZoneRule()

```c
I18n_ErrorCode OH_i18n_GetFirstStartFromTimeArrayTimeZoneRule(TimeArrayTimeZoneRule* rule, TimeZoneRuleQuery* query)
```

**Description**

Obtains the time when the TimeArrayTimeZoneRule first took effect.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md)* rule | Indicates the rule defined by TimeArrayTimeZoneRule[TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md). |
| [TimeZoneRuleQuery](capi-i18n-timezonerulequery.md)* query | Indicates the query information and query result. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes:      Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |

### OH_i18n_GetFirstStartFromAnnualTimeZoneRule()

```c
I18n_ErrorCode OH_i18n_GetFirstStartFromAnnualTimeZoneRule(AnnualTimeZoneRule* rule, TimeZoneRuleQuery* query)
```

**Description**

Obtains the time when the AnnualTimeZoneRule first took effect.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md)* rule | Indicates the rule defined by AnnualTimeZoneRule[AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md). |
| [TimeZoneRuleQuery](capi-i18n-timezonerulequery.md)* query | Indicates the query information and query result. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes:      Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |

### OH_i18n_GetFinalStartFromTimeArrayTimeZoneRule()

```c
I18n_ErrorCode OH_i18n_GetFinalStartFromTimeArrayTimeZoneRule(TimeArrayTimeZoneRule* rule, TimeZoneRuleQuery* query)
```

**Description**

Obtains the time when the TimeArrayTimeZoneRule final took effect.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md)* rule | Indicates the rule defined by TimeArrayTimeZoneRule[TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md). |
| [TimeZoneRuleQuery](capi-i18n-timezonerulequery.md)* query | Indicates the query information and query result. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes:      Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |

### OH_i18n_GetFinalStartFromAnnualTimeZoneRule()

```c
I18n_ErrorCode OH_i18n_GetFinalStartFromAnnualTimeZoneRule(AnnualTimeZoneRule* rule, TimeZoneRuleQuery* query)
```

**Description**

Obtains the time when the AnnualTimeZoneRule final took effect.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md)* rule | Indicates the rule defined by AnnualTimeZoneRule[AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md). |
| [TimeZoneRuleQuery](capi-i18n-timezonerulequery.md)* query | Indicates the query information and query result. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes:      Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |

### OH_i18n_GetNextStartFromTimeArrayTimeZoneRule()

```c
I18n_ErrorCode OH_i18n_GetNextStartFromTimeArrayTimeZoneRule(TimeArrayTimeZoneRule* rule, TimeZoneRuleQuery* query)
```

**Description**

Obtains the time when the TimeArrayTimeZoneRule next took effect.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md)* rule | Indicates the rule defined by TimeArrayTimeZoneRule[TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md). |
| [TimeZoneRuleQuery](capi-i18n-timezonerulequery.md)* query | Indicates the query information and query result. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes:      Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |

### OH_i18n_GetNextStartFromAnnualTimeZoneRule()

```c
I18n_ErrorCode OH_i18n_GetNextStartFromAnnualTimeZoneRule(AnnualTimeZoneRule* rule, TimeZoneRuleQuery* query)
```

**Description**

Obtains the time when the AnnualTimeZoneRule next took effect.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md)* rule | Indicates the rule defined by AnnualTimeZoneRule[AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md). |
| [TimeZoneRuleQuery](capi-i18n-timezonerulequery.md)* query | Indicates the query information and query result. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes:      Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |

### OH_i18n_GetPrevStartFromTimeArrayTimeZoneRule()

```c
I18n_ErrorCode OH_i18n_GetPrevStartFromTimeArrayTimeZoneRule(TimeArrayTimeZoneRule* rule, TimeZoneRuleQuery* query)
```

**Description**

Obtains the time when the TimeArrayTimeZoneRule previous took effect.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md)* rule | Indicates the rule defined by TimeArrayTimeZoneRule[TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md). |
| [TimeZoneRuleQuery](capi-i18n-timezonerulequery.md)* query | Indicates the query information and query result. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes:      Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |

### OH_i18n_GetPrevStartFromAnnualTimeZoneRule()

```c
I18n_ErrorCode OH_i18n_GetPrevStartFromAnnualTimeZoneRule(AnnualTimeZoneRule* rule, TimeZoneRuleQuery* query)
```

**Description**

Obtains the time when the AnnualTimeZoneRule previous took effect.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md)* rule | Indicates the rule defined by AnnualTimeZoneRule[AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md). |
| [TimeZoneRuleQuery](capi-i18n-timezonerulequery.md)* query | Indicates the query information and query result. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes:      Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |

### OH_i18n_GetStartTimeAt()

```c
I18n_ErrorCode OH_i18n_GetStartTimeAt(TimeArrayTimeZoneRule* rule, int32_t index, double* result)
```

**Description**

Obtain the effective start time of a specific rule in the TimeArrayTimeZoneRule.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md)* rule | Indicates the rule defined by TimeArrayTimeZoneRule[TimeArrayTimeZoneRule](capi-i18n-timearraytimezonerule.md). |
| int32_t index | Index of the start time. Value range: [0, rule.numStartTimes - 1]. |
| double* result | Time when the rule takes effect, in milliseconds. The value is Unix timestamp. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes:      Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |

### OH_i18n_GetStartInYear()

```c
I18n_ErrorCode OH_i18n_GetStartInYear(AnnualTimeZoneRule* rule, int32_t year, TimeZoneRuleQuery* query)
```

**Description**

Obtain the effective start time of a specific rule for target year in the AnnualTimeZoneRule.

**System capability**: SystemCapability.Global.I18n

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md)* rule | Indicates the rule defined by AnnualTimeZoneRule[AnnualTimeZoneRule](capi-i18n-annualtimezonerule.md). |
| int32_t year | Indicates the year used to get the rule defined by AnnualTimeZoneRule. |
| [TimeZoneRuleQuery](capi-i18n-timezonerulequery.md)* query | Indicates the query information and result. |

**Returns**:

| Type | Description |
| -- | -- |
| I18n_ErrorCode | [SUCCESS](capi-errorcode-h.md#i18n_errorcode) 0 - Success.          [ERROR_INVALID_PARAMETER](capi-errorcode-h.md#i18n_errorcode) 8900001 - Invalid parameter. Possible causes:      Parameter verification failed.          [UNEXPECTED_ERROR](capi-errorcode-h.md#i18n_errorcode) 8900050 - Unexpected error, such as memory error. |


