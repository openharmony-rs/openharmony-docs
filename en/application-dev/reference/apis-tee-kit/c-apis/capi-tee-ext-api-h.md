# tee_ext_api.h

## Overview

Provides extended interfaces.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ta_caller_info](capi-teetrusted-ta-caller-info.md) | caller_info | Defines the caller information. |

### Macro

| Name | Description |
| -- | -- |
| INVALID_USERID 0xFFFFFFFFU | Defines the value of invalid user ID.<br>**Since**: 20 |
| TEE_SMC_FROM_USR 0 | Defines the SMC from user mode.<br>**Since**: 20 |
| TEE_SMC_FROM_KERNEL 1 | Defines the SMC from kernel mode.<br>**Since**: 20 |
| RESERVED_BUF_SIZE 32 | Defines the size of reserved buffer.<br>**Since**: 20 |
| SESSION_FROM_CA   0 | Defines the session caller from CA.<br>**Since**: 20 |
| SESSION_FROM_TA   1 | Defines the session caller from TA.<br>**Since**: 20 |
| SESSION_FROM_NOT_SUPPORTED   0xFE | Defines the TA task is not found, for example, from TA sub thread.<br>**Since**: 20 |
| SESSION_FROM_UNKNOWN   0xFF | Defines the TA caller is not found.<br>**Since**: 20 |

### Function

| Name | Description |
| -- | -- |
| [TEE_Result tee_ext_get_caller_info(caller_info *caller_info_data, uint32_t length)](#tee_ext_get_caller_info) | Get caller info of current session, refer caller_info struct for more details. |
| [TEE_Result AddCaller_CA(const uint8_t *cainfo_hash, uint32_t length)](#addcaller_ca) | Adds information about a caller that can invoke this TA. This API applies to the client applications (CAs) in the native CA and HAP format. |
| [TEE_Result AddCaller_TA_all(void)](#addcaller_ta_all) | TA call this API allow others TA open session with itself. |
| [uint32_t tee_get_session_type(void)](#tee_get_session_type) | Obtains the session type. |

## Function description

### tee_ext_get_caller_info()

```c
TEE_Result tee_ext_get_caller_info(caller_info *caller_info_data, uint32_t length)
```

**Description**

Get caller info of current session, refer caller_info struct for more details.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [caller_info](capi-teetrusted-ta-caller-info.md) *[caller_info](capi-teetrusted-ta-caller-info.md)_data | A pointer to a buffer where the caller_info struct will be stored. |
| uint32_t length | The size of the buffer pointed to by caller_info_data. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### AddCaller_CA()

```c
TEE_Result AddCaller_CA(const uint8_t *cainfo_hash, uint32_t length)
```

**Description**

Adds information about a caller that can invoke this TA. This API applies to the client applications (CAs) in the native CA and HAP format.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const uint8_t *cainfo_hash | Indicates the hash value of the CA caller information. |
| uint32_t length | Indicates the length of the hash value. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### AddCaller_TA_all()

```c
TEE_Result AddCaller_TA_all(void)
```

**Description**

TA call this API allow others TA open session with itself.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful. |

### tee_get_session_type()

```c
uint32_t tee_get_session_type(void)
```

**Description**

Obtains the session type.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the session type obtained. |


