# OH_AVRecorder_Range
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_dyOv3Sds-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=f7deae3962affdf9350cd46c72e652967c8034c7 translatedAt=2026-09-15T16:38:45.586Z pushedAt=2026-09-18T09:27:01.800Z -->

```c
typedef struct OH_AVRecorder_Range {...} OH_AVRecorder_Range
```

## Overview

Defines the value range of AVRecorder parameters (such as the bit rate and frame rate) to limit the configurable range of recording parameters. You can use the [OH_AVRecorder_GetAvailableEncoder](capi-avrecorder-h.md#oh_avrecorder_getavailableencoder) API to obtain the value range of encoder parameters and set the parameter values within the range from **min** to **max** to ensure that the configuration is valid.

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t min | Minimum value of an AVRecorder parameter. The unit is the same as that of the described parameter. |
| int32_t max | Maximum value of an AVRecorder parameter. The unit is the same as that of the described parameter. |


