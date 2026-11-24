# TEE_Identity

```c
typedef struct TEE_Identity {...} TEE_Identity
```

## Overview

Definitions the TEE Identity.

<!--Device-typedef struct TEE_Identity {...} TEE_Identity--><!--Device-typedef struct TEE_Identity {...} TEE_Identity-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t login | Login method.<br><!--Device-uint32_t login--><!--Device-uint32_t login-End--> |
| [TEE_UUID](capi-teetrusted-tee-uuid.md) uuid | The UUID of the identity.<br><!--Device-TEE_UUID uuid--><!--Device-TEE_UUID uuid-End--> |


