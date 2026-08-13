# USBEndpoint

通过USB发送和接收数据的端口。通过[USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md#USBInterface)获取。 > **说明：** > > 主机控制器按照Endpoint类型调度。 > > 协议层打包时依赖type决定传输特性。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-usbManager-interface USBEndpoint--><!--Device-usbManager-interface USBEndpoint-End-->

**系统能力：** SystemCapability.USB.USBManager

## address

```TypeScript
address: int
```

端点地址。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBEndpoint-address: int--><!--Device-USBEndpoint-address: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## attributes

```TypeScript
attributes: int
```

端点属性。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBEndpoint-attributes: int--><!--Device-USBEndpoint-attributes: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## direction

```TypeScript
direction: USBRequestDirection
```

端点的方向。

**类型：** USBRequestDirection

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBEndpoint-direction: USBRequestDirection--><!--Device-USBEndpoint-direction: USBRequestDirection-End-->

**系统能力：** SystemCapability.USB.USBManager

## endpointAddr

```TypeScript
endpointAddr: int
```

Endpoint address

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBEndpoint-endpointAddr: int--><!--Device-USBEndpoint-endpointAddr: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## interfaceId

```TypeScript
interfaceId: int
```

端点所属的接口的唯一标识。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBEndpoint-interfaceId: int--><!--Device-USBEndpoint-interfaceId: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## interval

```TypeScript
interval: int
```

端点间隔。（单位：毫秒）

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBEndpoint-interval: int--><!--Device-USBEndpoint-interval: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## maxPacketSize

```TypeScript
maxPacketSize: int
```

端点最大数据包大小。（单位：字节）

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBEndpoint-maxPacketSize: int--><!--Device-USBEndpoint-maxPacketSize: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## number

```TypeScript
number: number
```

端点号。

**类型：** number

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-USBEndpoint-number: number--><!--Device-USBEndpoint-number: number-End-->

**系统能力：** SystemCapability.USB.USBManager

## type

```TypeScript
type: int
```

端点类型。取值见[UsbEndpointTransferType](arkts-basicservices-usbmanager-usbendpointtransfertype-e.md#UsbEndpointTransferType)

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-USBEndpoint-type: int--><!--Device-USBEndpoint-type: int-End-->

**系统能力：** SystemCapability.USB.USBManager

