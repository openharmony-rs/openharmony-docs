# DeviceInfo

播放设备的相关信息。

**起始版本：** 10

<!--Device-avSession-interface DeviceInfo--><!--Device-avSession-interface DeviceInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## authenticationStatus

```TypeScript
authenticationStatus?: number
```

播放设备是否可信。默认为0。0代表设备不可信，1代表设备可信。

**系统接口：** 该接口为系统接口。

**类型：** number

**起始版本：** 11

<!--Device-DeviceInfo-authenticationStatus?: int--><!--Device-DeviceInfo-authenticationStatus?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## hiPlayDeviceInfo

```TypeScript
hiPlayDeviceInfo?: HiPlayDeviceInfo
```

HiPlay设备类型定义

**类型：** HiPlayDeviceInfo

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceInfo-hiPlayDeviceInfo?: HiPlayDeviceInfo--><!--Device-DeviceInfo-hiPlayDeviceInfo?: HiPlayDeviceInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## ipAddress

```TypeScript
ipAddress?: string
```

播放设备的IP地址。

**系统接口：** 该接口为系统接口。

**类型：** string

**起始版本：** 10

<!--Device-DeviceInfo-ipAddress?: string--><!--Device-DeviceInfo-ipAddress?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## isLegacy

```TypeScript
isLegacy?: boolean
```

表示当前设备是否为旧版设备。 true表示是，false表示不是。

**系统接口：** 该接口为系统接口。

**类型：** boolean

**起始版本：** 13

<!--Device-DeviceInfo-isLegacy?: boolean--><!--Device-DeviceInfo-isLegacy?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## mediumTypes

```TypeScript
mediumTypes?: number
```

用于发现设备的介质类型。

1：蓝牙低功耗（BLE），用于蓝牙设备的发现和链接。

2：受限应用协议（COAP），用于局域网内的设备发现。

**系统接口：** 该接口为系统接口。

**类型：** number

**起始版本：** 13

<!--Device-DeviceInfo-mediumTypes?: int--><!--Device-DeviceInfo-mediumTypes?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
networkId?: string
```

播放设备的网络ID。

**系统接口：** 该接口为系统接口。

**类型：** string

**起始版本：** 13

<!--Device-DeviceInfo-networkId?: string--><!--Device-DeviceInfo-networkId?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## providerId

```TypeScript
providerId?: number
```

播放设备提供商。

**系统接口：** 该接口为系统接口。

**类型：** number

**起始版本：** 10

<!--Device-DeviceInfo-providerId?: int--><!--Device-DeviceInfo-providerId?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

