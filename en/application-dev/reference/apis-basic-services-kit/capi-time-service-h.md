# time_service.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: Time-->
<!--Owner: @huaxin05-->
<!--Designer: @hu-kai45-->
<!--Tester: @murphy1984-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=df07ef2b4f0aae6ba5e297d91b7ed3443ca2e961 translatedAt=2026-11-10T03:59:12.318Z pushedAt=2026-11-10T06:03:48.232Z nl=1 -->

## Overview

Declares the APIs for obtaining the time and time zone.

**Library**: libtime_service_ndk.so

**File to include**: <BasicServicesKit/time_service.h>

**System capability**: SystemCapability.MiscServices.Time

**Since**: 12

**Related module**: [TimeService](capi-timeservice.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [TimeService_ErrCode](#timeservice_errcode) | TimeService_ErrCode | Enumerates the error codes.|

### Functions

| Name| Description|
| -- | -- |
| [TimeService_ErrCode OH_TimeService_GetTimeZone(char *timeZone, uint32_t len)](#oh_timeservice_gettimezone) | Obtains the current system time zone.|

## Enum Description

### TimeService_ErrCode

```c
enum TimeService_ErrCode
```

**Description**

Enumerates the error codes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| TIMESERVICE_ERR_OK = 0 | Operation successful.|
| TIMESERVICE_ERR_INTERNAL_ERROR = 13000001 | Failed to obtain the system parameter. Try again later. If the problem persists, check the system service status. |
| TIMESERVICE_ERR_INVALID_PARAMETER = 13000002 | Invalid parameter. Check whether timeZone is a NULL pointer, or whether the size of the time zone name (excluding the terminator ('\0')) is greater than or equal to len. |


## Function Description

### OH_TimeService_GetTimeZone()

```c
TimeService_ErrCode OH_TimeService_GetTimeZone(char *timeZone, uint32_t len)
```

**Description**

Obtains the current system time zone.

**System capability**: SystemCapability.MiscServices.Time

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| char *timeZone | Character array for the time zone ID. On success, the current system time zone ID string is written to it. When timeZone is not NULL and the operation fails, an empty string is written to it. The string ends with '\0'. |
| uint32_t len | Size of the memory allocated for the time zone ID character array. There is no maximum length specification for the current time zone string. It is recommended to allocate sufficient memory, at least 31 bytes. When len is less than or equal to the actual length of the time zone string (excluding the terminator), TIMESERVICE_ERR_INVALID_PARAMETER is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [TimeService_ErrCode](#timeservice_errcode) | Returns `TIMESERVICE_ERR_OK` if the operation is successful.<br>Returns `TIMESERVICE_ERR_INTERNAL_ERROR` if obtaining the system parameter fails. Retry later. If the problem persists, check the system service status.<br>Returns `TIMESERVICE_ERR_INVALID_PARAMETER` if timeZone is a null pointer or the size of the time zone ID (excluding the terminating character ('\0')) is greater than or equal to len. Ensure that timeZone is a valid pointer and len is greater than the actual length of the time zone ID. |
