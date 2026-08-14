# CameraDevice

相机设备信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface CameraDevice--><!--Device-camera-interface CameraDevice-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## automotiveCameraPosition

```TypeScript
readonly automotiveCameraPosition?: AutomotiveCameraPosition
```

Car设备摄像头位置。

**类型：** [AutomotiveCameraPosition](arkts-camera-camera-automotivecameraposition-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly automotiveCameraPosition?: AutomotiveCameraPosition--><!--Device-CameraDevice-readonly automotiveCameraPosition?: AutomotiveCameraPosition-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## cameraId

```TypeScript
readonly cameraId: string
```

相机ID。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly cameraId: string--><!--Device-CameraDevice-readonly cameraId: string-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## cameraOrientation

```TypeScript
readonly cameraOrientation: int
```

相机安装角度，不会随着屏幕旋转而改变。取值范围为[0, 360]。单位：度。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly cameraOrientation: int--><!--Device-CameraDevice-readonly cameraOrientation: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## cameraPosition

```TypeScript
readonly cameraPosition: CameraPosition
```

相机位置。

**类型：** [CameraPosition](arkts-camera-camera-cameraposition-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly cameraPosition: CameraPosition--><!--Device-CameraDevice-readonly cameraPosition: CameraPosition-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## cameraType

```TypeScript
readonly cameraType: CameraType
```

相机类型。

**类型：** [CameraType](arkts-camera-camera-cameratype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly cameraType: CameraType--><!--Device-CameraDevice-readonly cameraType: CameraType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## connectionType

```TypeScript
readonly connectionType: ConnectionType
```

相机连接类型。

**类型：** [ConnectionType](arkts-camera-camera-connectiontype-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly connectionType: ConnectionType--><!--Device-CameraDevice-readonly connectionType: ConnectionType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## constituentCameraDevices

```TypeScript
readonly constituentCameraDevices?: Array<CameraDevice>
```

组成此逻辑相机的物理相机列表。

**类型：** Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly constituentCameraDevices?: Array<CameraDevice>--><!--Device-CameraDevice-readonly constituentCameraDevices?: Array<CameraDevice>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isLogicalCamera

```TypeScript
readonly isLogicalCamera?: boolean
```

是否为逻辑摄像头（由多个物理相机组成）, true表示是逻辑摄像头，false表示是物理摄像头。

**类型：** boolean

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly isLogicalCamera?: boolean--><!--Device-CameraDevice-readonly isLogicalCamera?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## lensDistortion

```TypeScript
readonly lensDistortion?: Array<double>
```

镜头畸变参数数组。

**类型：** Array&lt;double&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly lensDistortion?: Array<double>--><!--Device-CameraDevice-readonly lensDistortion?: Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## lensFocalLength

```TypeScript
readonly lensFocalLength?: double
```

镜头实际焦距。

**类型：** double

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly lensFocalLength?: double--><!--Device-CameraDevice-readonly lensFocalLength?: double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## lensIntrinsicCalibration

```TypeScript
readonly lensIntrinsicCalibration?: Array<double>
```

镜头内参标定参数数组。

**类型：** Array&lt;double&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly lensIntrinsicCalibration?: Array<double>--><!--Device-CameraDevice-readonly lensIntrinsicCalibration?: Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## minimumFocusDistance

```TypeScript
readonly minimumFocusDistance?: double
```

相机最小对焦距离。

**类型：** double

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly minimumFocusDistance?: double--><!--Device-CameraDevice-readonly minimumFocusDistance?: double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## sensorColorFilterArrangement

```TypeScript
readonly sensorColorFilterArrangement?: SensorColorFilterArrangement
```

传感器颜色滤镜排列方式。

**类型：** [SensorColorFilterArrangement](arkts-camera-camera-sensorcolorfilterarrangement-e.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly sensorColorFilterArrangement?: SensorColorFilterArrangement--><!--Device-CameraDevice-readonly sensorColorFilterArrangement?: SensorColorFilterArrangement-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## sensorPhysicalSize

```TypeScript
readonly sensorPhysicalSize?: Array<double>
```

传感器物理尺寸（宽度和高度）。

**类型：** Array&lt;double&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly sensorPhysicalSize?: Array<double>--><!--Device-CameraDevice-readonly sensorPhysicalSize?: Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## sensorPixelArraySize

```TypeScript
readonly sensorPixelArraySize?: Array<int>
```

传感器像素阵列尺寸（宽度和高度。单位：像素）。

**类型：** Array&lt;int&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-CameraDevice-readonly sensorPixelArraySize?: Array<int>--><!--Device-CameraDevice-readonly sensorPixelArraySize?: Array<int>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

