# ta_caller_info

```c
struct ta_caller_info {...}
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
| uint32_t session_type | The session type. |
| caller_identity..caller_uuid | The caller's UUID. |
| caller_identity..group_id | The caller's group ID. |
| caller_identity.ca_info | The buffer used to store CA information. |
| uint8_t smc_from_kernel_mode | Indicates whether the SMC is sent from kernel mode. |
| uint8_t reserved | Reserved buffer. |


