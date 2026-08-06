# CameraOcclusionDetectionResult

镜头遮挡或脏污检测回调返回的接口实例，表示镜头遮挡或脏污状态信息。

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-camera-interface CameraOcclusionDetectionResult--><!--Device-camera-interface CameraOcclusionDetectionResult-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isCameraLensDirty

```TypeScript
readonly isCameraLensDirty: boolean
```

镜头是否有脏污。true表示镜头有脏污，false表示镜头无脏污。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CameraOcclusionDetectionResult-readonly isCameraLensDirty: boolean--><!--Device-CameraOcclusionDetectionResult-readonly isCameraLensDirty: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isCameraOccluded

```TypeScript
readonly isCameraOccluded: boolean
```

镜头是否被遮挡。true表示镜头被遮挡，false表示镜头无遮挡。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CameraOcclusionDetectionResult-readonly isCameraOccluded: boolean--><!--Device-CameraOcclusionDetectionResult-readonly isCameraOccluded: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

