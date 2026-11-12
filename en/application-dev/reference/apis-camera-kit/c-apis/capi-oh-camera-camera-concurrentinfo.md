# Camera_ConcurrentInfo

```c
typedef struct Camera_ConcurrentInfo {...} Camera_ConcurrentInfo
```

## Overview

Concurrency capability infos.

<!--Device-struct Camera_ConcurrentInfo {...}--><!--Device-struct Camera_ConcurrentInfo {...}-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 18

**Related module**: [OH_Camera](capi-camera-kit-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Camera_Device](capi-oh-camera-camera-device.md) camera | Camera instance. |
| [Camera_ConcurrentType](capi-camera-h.md#camera_concurrenttype) type | Supported concurrent type. |
| [Camera_SceneMode](capi-camera-h.md#camera_scenemode)* sceneModes | Supported Modes. |
| [Camera_OutputCapability*](capi-oh-camera-camera-outputcapability.md) outputCapabilities | Supported outputCapabilities |
| uint32_t modeAndCapabilitySize | Supported outputCapabilities size. |


