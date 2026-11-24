# Camera_ConcurrentInfo

```c
typedef struct Camera_ConcurrentInfo {...} Camera_ConcurrentInfo
```

## 概述

相机并发能力信息。

<!--Device-struct Camera_ConcurrentInfo {...}--><!--Device-struct Camera_ConcurrentInfo {...}-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**起始版本：** 18

**相关模块：** [OH_Camera](capi-camera-kit-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Camera_Device](capi-oh-camera-camera-device.md) camera | 相机实例。<br><!--Device-Camera_Device camera--><!--Device-Camera_Device camera-End--> |
| [Camera_ConcurrentType](capi-camera-h.md#camera_concurrenttype) type | 相机并发状态。<br><!--Device-Camera_ConcurrentType type--><!--Device-Camera_ConcurrentType type-End--> |
| [Camera_SceneMode](capi-camera-h.md#camera_scenemode)* sceneModes | 相机并发支持的模式。<br><!--Device-Camera_SceneMode* sceneModes--><!--Device-Camera_SceneMode* sceneModes-End--> |
| [Camera_OutputCapability*](capi-oh-camera-camera-outputcapability.md) outputCapabilities | 相机输出能力集。<br><!--Device-Camera_OutputCapability* outputCapabilities--><!--Device-Camera_OutputCapability* outputCapabilities-End--> |
| uint32_t modeAndCapabilitySize | 相机输出能力集大小。<br><!--Device-uint32_t modeAndCapabilitySize--><!--Device-uint32_t modeAndCapabilitySize-End--> |


