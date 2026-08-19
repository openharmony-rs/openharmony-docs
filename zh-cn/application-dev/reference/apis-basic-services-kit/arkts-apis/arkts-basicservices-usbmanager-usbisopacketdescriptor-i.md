# UsbIsoPacketDescriptor

实时传输模式回调返回的分包信息。

**起始版本：** 23

<!--Device-usbManager-interface UsbIsoPacketDescriptor--><!--Device-usbManager-interface UsbIsoPacketDescriptor-End-->

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## actualLength

```TypeScript
actualLength: int
```

读写操作的实际长度值，（单位：字节）。

**类型：** int

**起始版本：** 23

<!--Device-UsbIsoPacketDescriptor-actualLength: int--><!--Device-UsbIsoPacketDescriptor-actualLength: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## length

```TypeScript
length: int
```

读写操作的期望长度值，（单位：字节）。

**类型：** int

**起始版本：** 23

<!--Device-UsbIsoPacketDescriptor-length: int--><!--Device-UsbIsoPacketDescriptor-length: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## status

```TypeScript
status: UsbTransferStatus
```

实时传输分包的状态码。

**类型：** [UsbTransferStatus](arkts-basicservices-usbmanager-usbtransferstatus-e.md)

**起始版本：** 23

<!--Device-UsbIsoPacketDescriptor-status: UsbTransferStatus--><!--Device-UsbIsoPacketDescriptor-status: UsbTransferStatus-End-->

**系统能力：** SystemCapability.USB.USBManager

