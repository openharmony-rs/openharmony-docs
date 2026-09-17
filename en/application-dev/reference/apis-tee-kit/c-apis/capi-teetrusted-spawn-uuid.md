# spawn_uuid

```c
typedef struct spawn_uuid {...} spawn_uuid_t
```

## Overview

Defines the type of spawn UUID.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t uuid_valid | Indicates if the UUID is valid. |
| [TEE_UUID](capi-teetrusted-tee-uuid.md) uuid | The spawn UUID. |


