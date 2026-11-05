# DRM_PsshInfo

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=6dec6b14cb206fe02a5ddd5033caa3930c0dd80f translatedAt=2026-11-04T04:20:41.644Z pushedAt=2026-11-04T10:12:50.087Z nl=1 -->

```c
typedef struct DRM_PsshInfo {...} DRM_PsshInfo
```

## Overview

The struct describes the Protection System Specific Header (PSSH) data for a DRM system.
 
**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t uuid[DRM_UUID_LEN] | UUID (Universal Unique Identifier) of the DRM system, used to uniquely identify a DRM content protection system. The UUID is 16 bytes long and is assigned by the DRM solution provider.|
| int32_t dataLen | Length of the PSSH data, indicating the number of valid bytes in the data array. The unit is byte, and the value range is [0, MAX_PSSH_DATA_LEN]. |
| uint8_t data[MAX_PSSH_DATA_LEN] | PSSH data, which contains DRM system-specific initialization data. The data format usually contains information such as the key ID and content ID. The array length is defined by the MAX_PSSH_DATA_LEN macro. |


