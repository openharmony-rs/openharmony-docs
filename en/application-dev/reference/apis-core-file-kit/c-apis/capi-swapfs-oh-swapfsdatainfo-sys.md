# OH_SwapfsDataInfo(System API)

```c
typedef struct OH_SwapfsDataInfo {...} OH_SwapfsDataInfo
```

## Overview

Information about a single swap key.

<!--Device-struct OH_SwapfsDataInfo {...}--><!--Device-struct OH_SwapfsDataInfo {...}-End-->

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [Swapfs](capi-core-file-kit-swapfs.md)

**Header file**: [oh_swapfs.h(System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t keyId | The keyId identifying this swap data entry.<br>**Since**: 26.0.0<br><!--Device-uint64_t keyId--><!--Device-uint64_t keyId-End--> |
| uint64_t dataSize | Original data size in bytes as provided by the caller during swap-out.<br>**Since**: 26.0.0<br><!--Device-uint64_t dataSize--><!--Device-uint64_t dataSize-End--> |
| uint64_t occupiedSize | File size in bytes occupied on disk. In DIO mode this is dataSize aligned up to SWAPFS_DIO_ALIGNMENT; in buffered mode it equals dataSize.<br>**Since**: 26.0.0<br><!--Device-uint64_t occupiedSize--><!--Device-uint64_t occupiedSize-End--> |
| int64_t createTime | Timestamp when the key was created (Unix epoch in milliseconds).<br>**Since**: 26.0.0<br><!--Device-int64_t createTime--><!--Device-int64_t createTime-End--> |
| OH_SwapfsKeyStatus status | Current status of the key.<br>**Since**: 26.0.0<br><!--Device-OH_SwapfsKeyStatus status--><!--Device-OH_SwapfsKeyStatus status-End--> |
| bool canSwapIn | Whether the key can be swapped in. False if the key is in REMOVING state.<br>**Since**: 26.0.0<br><!--Device-bool canSwapIn--><!--Device-bool canSwapIn-End--> |


