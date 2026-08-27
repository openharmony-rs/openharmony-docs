# CameraDevice

相机设备信息。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## automotiveCameraPosition

```TypeScript
readonly automotiveCameraPosition?: AutomotiveCameraPosition
```

Car设备摄像头位置。

**类型：** [AutomotiveCameraPosition](arkts-camera-camera-automotivecameraposition-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## cameraId

```TypeScript
readonly cameraId: string
```

相机ID。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## cameraOrientation

```TypeScript
readonly cameraOrientation: number
```

相机安装角度，不会随着屏幕旋转而改变。取值范围为[0, 360]。单位：度。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## cameraPosition

```TypeScript
readonly cameraPosition: CameraPosition
```

相机位置。

**类型：** [CameraPosition](arkts-camera-camera-cameraposition-e.md)

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## cameraType

```TypeScript
readonly cameraType: CameraType
```

相机类型。

**类型：** [CameraType](arkts-camera-camera-cameratype-e.md)

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## connectionType

```TypeScript
readonly connectionType: ConnectionType
```

相机连接类型。

**类型：** [ConnectionType](arkts-camera-camera-connectiontype-e.md)

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## constituentCameraDevices

```TypeScript
readonly constituentCameraDevices?: Array<CameraDevice>
```

组成此逻辑相机的物理相机列表。

**类型：** Array&lt;[CameraDevice](arkts-camera-camera-cameradevice-i.md)&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## hostDeviceName

```TypeScript
readonly hostDeviceName: string
```

远端设备名称。若当前无远端设备，返回为空。

**类型：** string

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## hostDeviceType

```TypeScript
readonly hostDeviceType: HostDeviceType
```

远端设备类型。

**类型：** [HostDeviceType](arkts-camera-camera-hostdevicetype-e.md)

**起始版本：** 15

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isLogicalCamera

```TypeScript
readonly isLogicalCamera?: boolean
```

是否为逻辑摄像头（由多个物理相机组成）, true表示是逻辑摄像头，false表示是物理摄像头。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## lensDistortion

```TypeScript
readonly lensDistortion?: Array<number>
```

镜头畸变参数数组。

**类型：** Array&lt;number&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## lensEquivalentFocalLength

```TypeScript
readonly lensEquivalentFocalLength?: Array<number>
```

相机镜头等效焦距。

**类型：** Array&lt;number&gt;

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## lensFocalLength

```TypeScript
readonly lensFocalLength?: number
```

镜头实际焦距。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## lensIntrinsicCalibration

```TypeScript
readonly lensIntrinsicCalibration?: Array<number>
```

镜头内参标定参数数组。

**类型：** Array&lt;number&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## minimumFocusDistance

```TypeScript
readonly minimumFocusDistance?: number
```

相机最小对焦距离。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## sensorColorFilterArrangement

```TypeScript
readonly sensorColorFilterArrangement?: SensorColorFilterArrangement
```

传感器颜色滤镜排列方式。

**类型：** [SensorColorFilterArrangement](arkts-camera-camera-sensorcolorfilterarrangement-e.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## sensorPhysicalSize

```TypeScript
readonly sensorPhysicalSize?: Array<number>
```

传感器物理尺寸（宽度和高度）。

**类型：** Array&lt;number&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## sensorPixelArraySize

```TypeScript
readonly sensorPixelArraySize?: Array<number>
```

传感器像素阵列尺寸（宽度和高度。单位：像素）。

**类型：** Array&lt;number&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core
