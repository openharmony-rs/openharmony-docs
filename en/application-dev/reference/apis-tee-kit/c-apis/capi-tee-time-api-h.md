# tee_time_api.h

## Overview

Provides APIs for managing the Trusted Execution Environment (TEE) time.<br> You can use these APIs to implement time-related features in a TEE.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

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
| TEE_Time *time | Indicates the pointer to the current system time obtained. |

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
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

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
| TEE_Time *time | Indicates the pointer to the persistent time of the TA. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

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
| TEE_Time *time | Indicates the pointer to the persistent time of the TA. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

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
| TEE_Time *time | Indicates the pointer to the REE system time obtained. |


