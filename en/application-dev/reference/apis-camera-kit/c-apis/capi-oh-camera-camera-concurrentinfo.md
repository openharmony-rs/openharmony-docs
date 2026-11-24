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
| [Camera_Device](capi-oh-camera-camera-device.md) camera | Camera instance.<br><!--Device-Camera_Device camera--><!--Device-Camera_Device camera-End--> |
| [Camera_ConcurrentType](capi-camera-h.md#camera_concurrenttype) type | Supported concurrent type.<br><!--Device-Camera_ConcurrentType type--><!--Device-Camera_ConcurrentType type-End--> |
| [Camera_SceneMode](capi-camera-h.md#camera_scenemode)* sceneModes | Supported Modes.<br><!--Device-Camera_SceneMode* sceneModes--><!--Device-Camera_SceneMode* sceneModes-End--> |
| [Camera_OutputCapability*](capi-oh-camera-camera-outputcapability.md) outputCapabilities | Supported outputCapabilities<br><!--Device-Camera_OutputCapability* outputCapabilities--><!--Device-Camera_OutputCapability* outputCapabilities-End--> |
| uint32_t modeAndCapabilitySize | Supported outputCapabilities size.<br><!--Device-uint32_t modeAndCapabilitySize--><!--Device-uint32_t modeAndCapabilitySize-End--> |


