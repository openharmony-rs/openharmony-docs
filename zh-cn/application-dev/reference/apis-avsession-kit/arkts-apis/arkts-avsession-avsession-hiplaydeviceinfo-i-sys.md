# HiPlayDeviceInfo（系统接口）

HiPlay 设备类型定义

**起始版本：** 24

<!--Device-avSession-interface HiPlayDeviceInfo--><!--Device-avSession-interface HiPlayDeviceInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## castMode

```TypeScript
castMode?: number
```

HiPlay 投播模式，设备级和应用级

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-HiPlayDeviceInfo-castMode?: int--><!--Device-HiPlayDeviceInfo-castMode?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## castUid

```TypeScript
castUid?: number
```

HiPlay 当前投播uid

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-HiPlayDeviceInfo-castUid?: int--><!--Device-HiPlayDeviceInfo-castUid?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## supportCastMode

```TypeScript
supportCastMode?: number
```

支持的Cast Mode，包含设备级和应用级投播

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-HiPlayDeviceInfo-supportCastMode?: int--><!--Device-HiPlayDeviceInfo-supportCastMode?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## supportMultiDeviceMode

```TypeScript
supportMultiDeviceMode?: number
```

是否支持多设备连接能力。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务API中使用。

<!--Device-HiPlayDeviceInfo-supportMultiDeviceMode?: int--><!--Device-HiPlayDeviceInfo-supportMultiDeviceMode?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

