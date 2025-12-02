# DRM_PsshInfo

## Overview

The struct describes the Protection System Specific Header (PSSH) data for a DRM system.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t uuid[DRM_UUID_LEN] | UUID identifying the DRM system for the PSSH data.|
| int32_t dataLen | Length of the PSSH data payload.|
| uint8_t data[MAX_PSSH_DATA_LEN] | PSSH data payload.|
