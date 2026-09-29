# spawn_uuid

```c
struct spawn_uuid {...}
```

## Overview

Defines the type of spawn UUID.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t uuid_valid | Indicates if the UUID is valid. |
| TEE_UUID uuid | The spawn UUID. |


