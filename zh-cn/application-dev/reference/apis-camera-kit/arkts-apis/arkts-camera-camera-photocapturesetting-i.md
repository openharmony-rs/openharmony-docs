# PhotoCaptureSetting

拍摄照片的设置。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## compressionQuality

```TypeScript
compressionQuality?: number
```

图片压缩质量值，取值范围为(1, 100)。当compressionQuality未下发时，默认按quality生效；若quality与compressionQuality同时下发则按compressionQuality下发生效；若quality与 compressionQuality均未下发则图片质量默认是高等。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## location

```TypeScript
location?: Location
```

图片地理位置信息（默认以设备硬件信息为准）。

**类型：** Location

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## mirror

```TypeScript
mirror?: boolean
```

镜像使能开关（默认关）。使用之前需要使用[isMirrorSupported](arkts-camera-camera-photooutput-i.md#ismirrorsupported)进行判断是否支持。true表示使能，false表示不使能。

**类型：** boolean

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## quality

```TypeScript
quality?: QualityLevel
```

图片质量。当quality未下发时，默认按compressionQuality下发生效；若quality与compressionQuality同时下发则按compressionQuality下发生效；若quality与 compressionQuality均未下发则图片质量默认是高等。

**类型：** QualityLevel

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## rotation

```TypeScript
rotation?: ImageRotation
```

图片旋转角度（默认0度，顺时针旋转）。

**类型：** [ImageRotation](arkts-camera-camera-imagerotation-e.md)

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core
