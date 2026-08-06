# MetadataBasicFaceObject

相机检测到的基础人脸元数据信息，继承自[MetadataObject]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。[CameraInput]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_相机信息中的数据来源， 通过metadataOutput. [on('metadataObjectsAvailable')]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_ 接口获取。

**继承/实现关系：** MetadataBasicFaceObject extends [MetadataObject](arkts-camera-camera-metadataobject-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-camera-interface MetadataBasicFaceObject extends MetadataObject--><!--Device-camera-interface MetadataBasicFaceObject extends MetadataObject-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## leftEyeBoundingBox

```TypeScript
readonly leftEyeBoundingBox?: Rect
```

左眼区域框。

**类型：** Rect

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataBasicFaceObject-readonly leftEyeBoundingBox?: Rect--><!--Device-MetadataBasicFaceObject-readonly leftEyeBoundingBox?: Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## pitchAngle

```TypeScript
readonly pitchAngle?: int
```

俯仰角度。取值范围为[-90, 90]，以向下为正方向。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataBasicFaceObject-readonly pitchAngle?: int--><!--Device-MetadataBasicFaceObject-readonly pitchAngle?: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## rightEyeBoundingBox

```TypeScript
readonly rightEyeBoundingBox?: Rect
```

右眼区域框。

**类型：** Rect

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataBasicFaceObject-readonly rightEyeBoundingBox?: Rect--><!--Device-MetadataBasicFaceObject-readonly rightEyeBoundingBox?: Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## rollAngle

```TypeScript
readonly rollAngle?: int
```

平面内旋转角度。取值范围为[-180, 180]，以顺时针方向为正方向。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataBasicFaceObject-readonly rollAngle?: int--><!--Device-MetadataBasicFaceObject-readonly rollAngle?: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## yawAngle

```TypeScript
readonly yawAngle?: int
```

左右旋转角度。取值范围为[-90, 90]，以向右为正方向。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-MetadataBasicFaceObject-readonly yawAngle?: int--><!--Device-MetadataBasicFaceObject-readonly yawAngle?: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

