# ta_caller_info

```c
typedef struct ta_caller_info {...} caller_info
```

## Overview

Defines the caller information.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_ext_api.h](capi-tee-ext-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t session_type;
 union | The session type. |
| TEE_UUID caller_uuid | The caller's UUID. |
| uint32_t group_id;
 } | The caller's group ID. |
| uint8_t ca_info[RESERVED_BUF_SIZE];
 } caller_identity | The buffer used to store CA information. |
| uint8_t smc_from_kernel_mode | Indicates whether the SMC is sent from kernel mode. |
| uint8_t reserved[RESERVED_BUF_SIZE - 1] | Reserved buffer. |


