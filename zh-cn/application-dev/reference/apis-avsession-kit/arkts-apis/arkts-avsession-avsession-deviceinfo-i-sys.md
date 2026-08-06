# DeviceInfo

播放设备的相关信息。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-avSession-interface DeviceInfo--><!--Device-avSession-interface DeviceInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## authenticationStatus

```TypeScript
authenticationStatus?: int
```

播放设备是否可信。默认为0。0代表设备不可信，1代表设备可信。 **系统接口：** 该接口为系统接口。

**类型：** int

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

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

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceInfo-hiPlayDeviceInfo?: HiPlayDeviceInfo--><!--Device-DeviceInfo-hiPlayDeviceInfo?: HiPlayDeviceInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## ipAddress

```TypeScript
ipAddress?: string
```

播放设备的IP地址。 **系统接口：** 该接口为系统接口。

**类型：** string

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-DeviceInfo-ipAddress?: string--><!--Device-DeviceInfo-ipAddress?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## isLegacy

```TypeScript
isLegacy?: boolean
```

表示当前设备是否为旧版设备。 true表示是，false表示不是。 **系统接口：** 该接口为系统接口。

**类型：** boolean

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-DeviceInfo-isLegacy?: boolean--><!--Device-DeviceInfo-isLegacy?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## mediumTypes

```TypeScript
mediumTypes?: int
```

用于发现设备的介质类型。 1：蓝牙低功耗（BLE），用于蓝牙设备的发现和链接。 2：受限应用协议（COAP），用于局域网内的设备发现。 **系统接口：** 该接口为系统接口。

**类型：** int

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-DeviceInfo-mediumTypes?: int--><!--Device-DeviceInfo-mediumTypes?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## networkId

```TypeScript
networkId?: string
```

播放设备的网络ID。 **系统接口：** 该接口为系统接口。

**类型：** string

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

<!--Device-DeviceInfo-networkId?: string--><!--Device-DeviceInfo-networkId?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

## providerId

```TypeScript
providerId?: int
```

播放设备提供商。 **系统接口：** 该接口为系统接口。

**类型：** int

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-DeviceInfo-providerId?: int--><!--Device-DeviceInfo-providerId?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

