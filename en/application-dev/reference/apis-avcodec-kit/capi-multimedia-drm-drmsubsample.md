# DrmSubsample

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhanghongran-->
<!--Designer: @dpy2650--->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

```
typedef struct DrmSubsample {...} DrmSubsample
```

## Overview

The struct describes the subsample type.

**Since**: 12

**Related module**: [Multimedia_Drm](capi-multimedia-drm.md)

**Header file**: [native_cencinfo.h](capi-native-cencinfo-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t clearHeaderLen | Length of the clear header.|
| uint32_t payLoadLen | Length of the encrypted payload.|
