# TEE_Identity

```c
typedef struct TEE_Identity {...} TEE_Identity
```

## Overview

Definitions the TEE Identity.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t login | Login method. |
| [TEE_UUID](capi-teetrusted-tee-uuid.md) uuid | The UUID of the identity. |


