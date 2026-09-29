# tee_time_api.h

## Overview

Provides APIs for managing the Trusted Execution Environment (TEE) time.<br> You can use these APIs to implement time-related features in a TEE.

**Library**: NA

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [void TEE_GetSystemTime(TEE_Time *time)](#tee_getsystemtime) | Obtains the current TEE system time. |
| [TEE_Result TEE_Wait(uint32_t timeout)](#tee_wait) | Waits for the specified period of time, in milliseconds. |
| [TEE_Result TEE_GetTAPersistentTime(TEE_Time *time)](#tee_gettapersistenttime) | Obtains the persistent time of this trusted application (TA). |
| [TEE_Result TEE_SetTAPersistentTime(TEE_Time *time)](#tee_settapersistenttime) | Sets the persistent time for this TA. |
| [void TEE_GetREETime(TEE_Time *time)](#tee_getreetime) | Obtains the current Rich Execution Environment (REE) system time. |

## Function description

### TEE_GetSystemTime()

```c
void TEE_GetSystemTime(TEE_Time *time)
```

**Description**

Obtains the current TEE system time.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [TEE_Time](capi-teetrusted-tee-time.md) *time | Indicates the pointer to the current system time obtained. |

### TEE_Wait()

```c
TEE_Result TEE_Wait(uint32_t timeout)
```

**Description**

Waits for the specified period of time, in milliseconds.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t timeout | Indicates the period of time to wait, in milliseconds. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. Returns <b>TEE_ERROR_CANCEL</b> if the wait is canceled. Returns <b>TEE_ERROR_OUT_OF_MEMORY</b> if the memory is not sufficient to complete the operation. |

### TEE_GetTAPersistentTime()

```c
TEE_Result TEE_GetTAPersistentTime(TEE_Time *time)
```

**Description**

Obtains the persistent time of this trusted application (TA).

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [TEE_Time](capi-teetrusted-tee-time.md) *time | Indicates the pointer to the persistent time of the TA. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. Returns <b>TEE_ERROR_TIME_NOT_SET</b> if the persistent time has not been set. Returns <b>TEE_ERROR_TIME_NEEDS_RESET</b> if the persistent time is corrupted and the application is not longer trusted. Returns <b>TEE_ERROR_OVERFLOW</b> if the number of seconds in the TA persistent time exceeds the range of <b>uint32_t</b>. Returns <b>TEE_ERROR_OUT_OF_MEMORY</b> if the memory is not sufficient to complete the operation. |

### TEE_SetTAPersistentTime()

```c
TEE_Result TEE_SetTAPersistentTime(TEE_Time *time)
```

**Description**

Sets the persistent time for this TA.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [TEE_Time](capi-teetrusted-tee-time.md) *time | Indicates the pointer to the persistent time of the TA. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. Returns <b>TEE_ERROR_OUT_OF_MEMORY</b> if the memory is not sufficient to complete the operation. Returns <b>TEE_ERROR_STORAGE_NO_SPACE</b> if the storage space is not sufficient to complete the operation. |

### TEE_GetREETime()

```c
void TEE_GetREETime(TEE_Time *time)
```

**Description**

Obtains the current Rich Execution Environment (REE) system time.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [TEE_Time](capi-teetrusted-tee-time.md) *time | Indicates the pointer to the REE system time obtained. |


