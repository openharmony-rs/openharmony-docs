# Camera_ConcurrentInfo

```c
typedef struct Camera_ConcurrentInfo {...} Camera_ConcurrentInfo
```

## Overview

Concurrency capability infos.

**Since**: 18

**Related module**: [OH_Camera](capi-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Camera_Device](capi-oh-camera-camera-device.md) camera | Camera instance. |
| [Camera_ConcurrentType](capi-camera-h.md#camera_concurrenttype) type | Supported concurrent type. |
| Camera_SceneMode* sceneModes | Supported Modes. |
| [Camera_OutputCapability*](capi-oh-camera-camera-outputcapability.md) outputCapabilities | Supported outputCapabilities |
| uint32_t modeAndCapabilitySize | Supported outputCapabilities size. |


