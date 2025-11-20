# DRM_MediaKeySystemInfo

## Overview

The struct describes the DRM information for encrypted content.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t psshCount | Number of Protection Scheme Specific Header (PSSH) data entries.|
| [DRM_PsshInfo](capi-drm-drm-psshinfo.md) psshInfo[MAX_PSSH_INFO_COUNT] | Array containing PSSH data entries.|
