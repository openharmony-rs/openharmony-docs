# ExposureMode

枚举，曝光模式。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Camera.Core

## EXPOSURE_MODE_UNSPECIFIED

```TypeScript
EXPOSURE_MODE_UNSPECIFIED = -1
```

曝光模式未指定。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## EXPOSURE_MODE_LOCKED

```TypeScript
EXPOSURE_MODE_LOCKED = 0
```

锁定曝光模式。不支持曝光区域中心点设置。设置该模式后，每次拍照时曝光都会默认锁定。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## EXPOSURE_MODE_AUTO

```TypeScript
EXPOSURE_MODE_AUTO = 1
```

自动曝光模式。支持曝光区域中心点设置，可以使用[AutoExposure.setMeteringPoint](arkts-camera-camera-autoexposure-i.md#setmeteringpoint)接口设置曝光区域中心点。设置该模式后，仅设置后的首次拍照生效。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## EXPOSURE_MODE_CONTINUOUS_AUTO

```TypeScript
EXPOSURE_MODE_CONTINUOUS_AUTO = 2
```

连续自动曝光。不支持曝光区域中心点设置。设置该模式后，拍照系统会根据每次的环境变化自动调整曝光。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

## EXPOSURE_MODE_MANUAL

```TypeScript
EXPOSURE_MODE_MANUAL = 3
```

手动曝光。支持设置曝光时长。设置该模式后，用户可通过 [ManualExposure.setExposureDuration](../../../reference/apis-camera-kit/arkts-apis-camera-ManualExposure.md#setexposureduration) 设置曝光时长。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core
