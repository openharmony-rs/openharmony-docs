# OH_AVRecorder_Range

```c
typedef struct OH_AVRecorder_Range {...} OH_AVRecorder_Range
```

## Overview

Defines the value range of AVRecorder parameters (such as the bit rate and frame rate) to limit the configurable range of recording parameters. You can use the [OH_AVRecorder_GetAvailableEncoder][OH_AVRecorder_GetAvailableEncoder](capi-avrecorder-h.md#oh_avrecorder_getavailableencoder) API to obtain the value range of encoder parameters and set the parameter values within the range from **min** to **max** to ensure that the configuration is valid.

<!--Device-struct OH_AVRecorder_Range {...}--><!--Device-struct OH_AVRecorder_Range {...}-End-->

**Since**: 18

**Related module**: [AVRecorder](capi-media-kit-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t min | Minimum value of an AVRecorder parameter. The unit is the same as that of the described parameter.<br>**Since**: 18 |
| int32_t max | Maximum value of an AVRecorder parameter. The unit is the same as that of the described parameter.<br>**Since**: 18 |


