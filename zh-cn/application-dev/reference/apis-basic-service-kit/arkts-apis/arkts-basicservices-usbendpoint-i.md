# USBEndpoint

通过USB发送和接收数据的端口。通过[USBInterface](arkts-basicservices-usbinterface-i.md)获取。

> **说明：**
>
> 主机控制器按照Endpoint类型调度。
>
> 协议层打包时依赖type决定传输特性。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## address

```TypeScript
address: number
```

端点地址。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## attributes

```TypeScript
attributes: number
```

端点属性。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## direction

```TypeScript
direction: USBRequestDirection
```

端点的方向。

**类型：** USBRequestDirection

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## interfaceId

```TypeScript
interfaceId: number
```

端点所属的接口的唯一标识。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## interval

```TypeScript
interval: number
```

端点间隔。（单位：毫秒）

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## maxPacketSize

```TypeScript
maxPacketSize: number
```

端点最大数据包大小。（单位：字节）

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## number

```TypeScript
number: number
```

端点号。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## type

```TypeScript
type: number
```

端点类型。取值见[UsbEndpointTransferType](arkts-basicservices-usbendpointtransfertype-e.md)

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

