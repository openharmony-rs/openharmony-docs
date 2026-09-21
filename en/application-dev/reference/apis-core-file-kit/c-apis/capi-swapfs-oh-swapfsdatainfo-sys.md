# OH_SwapfsDataInfo(System API)

```c
typedef struct OH_SwapfsDataInfo {...} OH_SwapfsDataInfo
```

## Overview

Information about a single swap key.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [Swapfs](capi-swapfs.md)

**Header file**: [oh_swapfs.h(System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t keyId | The keyId identifying this swap data entry.<br>**Since**: 26.0.0 |
| uint64_t dataSize | Original data size in bytes as provided by the caller during swap-out.<br>**Since**: 26.0.0 |
| uint64_t occupiedSize | File size in bytes occupied on disk. In DIO mode this is dataSize aligned up to SWAPFS_DIO_ALIGNMENT; in buffered mode it equals dataSize.<br>**Since**: 26.0.0 |
| int64_t createTime | Timestamp when the key was created (Unix epoch in milliseconds).<br>**Since**: 26.0.0 |
| [OH_SwapfsKeyStatus](capi-oh-swapfs-h-sys.md#oh_swapfskeystatus) status | Current status of the key.<br>**Since**: 26.0.0 |
| bool canSwapIn | Whether the key can be swapped in. False if the key is in REMOVING state.<br>**Since**: 26.0.0 |


