# OH_OnFrameAvailableListener

```c
typedef struct OH_OnFrameAvailableListener {...} OH_OnFrameAvailableListener
```

## Overview

A listener for native image, use <b>OH_NativeImage_SetOnFrameAvailableListener</b> to register the listener object to <b>OH_NativeImage</b>, the callback will be triggered when there is available frame

**System capability**: SystemCapability.Graphic.Graphic2D.NativeImage

**Since**: 11

**Related module**: [OH_NativeImage](capi-oh-nativeimage.md)

**Header file**: [native_image.h](capi-native-image-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *context | User defined context, returned to the user in the callback function |
| [OH_OnFrameAvailable](capi-native-image-h.md#oh_onframeavailable) onFrameAvailable | The callback function of frame available. |


