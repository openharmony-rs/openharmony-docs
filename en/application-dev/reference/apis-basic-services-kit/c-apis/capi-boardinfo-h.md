# boardinfo.h

## Overview

Declares the APIs for query hardware device information.

**File to Include**: <boardinfo.h>

**Library**: libboardinfo_ndk.z.so

**System capability**: SystemCapability.Startup.BoardInfo

**Since**: 26.1.0

**Related module**: [BoardInfo](capi-basic-services-kit-boardinfo.md)

## Summary

### Functions

| Name | Description |
| -- | -- |
| [const char *OH_BoardInfo_GetCpuId(void)](#oh_boardinfo_getcpuid) | Obtains the device CPUID. |
| [int32_t OH_BoardInfo_GetBoardSn(char *boardSn)](#oh_boardinfo_getboardsn) | The value of Sn.value len of the obtained device is 16. The size of the parameter buffer cannot be less than 17 bytes(including the terminator). ** Required Permissions **:ohos.permission.ACCESS_BOARD_INFO |

## Function description

### OH_BoardInfo_GetCpuId()

```c
const char *OH_BoardInfo_GetCpuId(void)
```

**Description**

Obtains the device CPUID.

<!--Device-const char *OH_BoardInfo_GetCpuId(void)--><!--Device-const char *OH_BoardInfo_GetCpuId(void)-End-->

**System capability**: SystemCapability.Startup.BoardInfo

**Since**: 26.1.0

**Returns**:

| Type | Description |
| -- | -- |
| const char * | Returns a device CPUID. The value is of the string type. |

### OH_BoardInfo_GetBoardSn()

```c
int32_t OH_BoardInfo_GetBoardSn(char *boardSn)
```

**Description**

The value of Sn.value len of the obtained device is 16. The size of the parameter buffer cannot be less than 17 bytes(including the terminator). ** Required Permissions **:ohos.permission.ACCESS_BOARD_INFO

<!--Device-int32_t OH_BoardInfo_GetBoardSn(char *boardSn)--><!--Device-int32_t OH_BoardInfo_GetBoardSn(char *boardSn)-End-->

**System capability**: SystemCapability.Startup.BoardInfo

**Required permission**: ohos.permission.ACCESS_BOARD_INFO

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| char *boardSn | [out] Serial number of the board. The buffer size cannot be less than 17 bytes(including the terminator). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul> <li>0 if the operation is successful.</li> <li>201 if the caller does not have ohos.permission.ACCESS_BOARD_INFO.</li> <li>401 If the caller passes null or invalid parameters.</li> </ul> |


