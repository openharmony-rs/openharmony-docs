# ta_caller_info

```c
typedef struct ta_caller_info {...} caller_info
```

## Overview

Defines the caller information.

<!--Device-struct ta_caller_info {...}--><!--Device-struct ta_caller_info {...}-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_ext_api.h](capi-tee-ext-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t session_type | The session type.<br><!--Device-uint32_t session_type--><!--Device-uint32_t session_type-End--> |
| caller_identity..caller_uuid | The caller's UUID.<br><!--Device-caller_identity..caller_uuid--><!--Device-caller_identity..caller_uuid-End--> |
| caller_identity..group_id | The caller's group ID.<br><!--Device-caller_identity..group_id--><!--Device-caller_identity..group_id-End--> |
| caller_identity.ca_info | The buffer used to store CA information.<br><!--Device-caller_identity.ca_info--><!--Device-caller_identity.ca_info-End--> |
| uint8_t smc_from_kernel_mode | Indicates whether the SMC is sent from kernel mode.<br><!--Device-uint8_t smc_from_kernel_mode--><!--Device-uint8_t smc_from_kernel_mode-End--> |
| uint8_t reserved[RESERVED_BUF_SIZE - 1] | Reserved buffer.<br><!--Device-uint8_t reserved[RESERVED_BUF_SIZE - 1]--><!--Device-uint8_t reserved[RESERVED_BUF_SIZE - 1]-End--> |


