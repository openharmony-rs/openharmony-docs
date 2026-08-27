# USBEndpoint

USB端点，用于主机与设备之间数据传输的通信端点。通过[USBInterface](arkts-basicservices-usbmanager-usbinterface-i.md)获取。

> **说明：**
> 
> 主机控制器按照Endpoint类型调度，不同类型的端点采用不同的调度策略：批量端点(bulk)采用带宽共享调度适合大量数据非实时传输；中断端点(interrupt)采用固定轮询调度适合小数据量实时传输；实时端点(
> isochronous)采用带宽预留调度，适合音视频等实时数据流。
> 
> 协议层打包时依赖type决定传输特性，包括数据包格式、错误处理机制、超时策略等。


**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
```

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

端点属性，表示端点的传输特性，包括传输类型（批量、中断、实时）和同步类型等。取值遵循USB端点描述符规范。

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

端点间隔。中断端点和实时端点为时间间隔（单位：毫秒）；批量端点不使用此字段。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## maxPacketSize

```TypeScript
maxPacketSize: number
```

端点最大数据包大小，（单位：字节）。

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

端点类型。取值见[UsbEndpointTransferType](arkts-basicservices-usbmanager-usbendpointtransfertype-e.md)

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager
