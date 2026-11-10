# spawn_uuid

```c
struct spawn_uuid {...}
```

## Overview

Defines the type of spawn UUID.

<!--Device-struct spawn_uuid {...}--><!--Device-struct spawn_uuid {...}-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t uuid_valid | Indicates if the UUID is valid. |
| TEE_UUID uuid | The spawn UUID. |


