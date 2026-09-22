# time_service.h

## Overview

Declares the APIs for obtaining the time zone information.

**Library**: libtime_service_ndk.so

**System capability**: SystemCapability.MiscServices.Time

**Since**: 12

**Related module**: [TimeService](capi-timeservice.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [TimeService_ErrCode](#timeservice_errcode) | TimeService_ErrCode | Enumerates the error codes. |

### Macro

| Name | Description |
| -- | -- |
| TIME_SERVICE_H | Declares the APIs for obtaining the time zone information.<br>**Since**: 12<br>**System capability**: SystemCapability.MiscServices.Time |

### Function

| Name | Description |
| -- | -- |
| [TimeService_ErrCode OH_TimeService_GetTimeZone(char *timeZone, uint32_t len)](#oh_timeservice_gettimezone) | Obtains the current system time zone. |

## Enum type description

### TimeService_ErrCode

```c
enum TimeService_ErrCode
```

**Description**

Enumerates the error codes.

**System capability**: SystemCapability.MiscServices.Time

**Since**: 12

| Enum item | Description |
| -- | -- |
| TIMESERVICE_ERR_OK = 0 | Operation successful. |
| TIMESERVICE_ERR_INTERNAL_ERROR = 13000001 | Failed to obtain system parameters. |
| TIMESERVICE_ERR_INVALID_PARAMETER = 13000002 | Invalid parameter. |


## Function description

### OH_TimeService_GetTimeZone()

```c
TimeService_ErrCode OH_TimeService_GetTimeZone(char *timeZone, uint32_t len)
```

**Description**

Obtains the current system time zone.

**System capability**: SystemCapability.MiscServices.Time

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *timeZone | Pointer to the buffer for one time zone ID string. If the time zone is obtained, its ID is written. Otherwise, an empty string is written. The string ends with **\0**. |
| uint32_t len | Capacity of the buffer pointed to by **timeZone**, in bytes, including the end character **\0**. There is no maximum limit. You are advised to allocate at least 31 bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| [TimeService_ErrCode](capi-time-service-h.md#timeservice_errcode) | Returns TIMESERVICE_ERR_OK if the operation is successful;      <br>returns TIMESERVICE_ERR_INTERNAL_ERROR if the system parameters fail to be obtained;      <br>returns TIMESERVICE_ERR_INVALID_PARAMETER if timeZone is a null pointer or the length of the time      zone name (excluding the end character \0) is greater than or equal to the value of len. |


