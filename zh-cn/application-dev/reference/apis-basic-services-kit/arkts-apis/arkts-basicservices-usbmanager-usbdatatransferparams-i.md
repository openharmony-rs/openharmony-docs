# UsbDataTransferParams

USB数据传输参数对象，包含USB数据传输所需的所有参数，用于usbSubmitTransfer和usbCancelTransfer接口发起传输请求。

**起始版本：** 23

<!--Device-usbManager-interface UsbDataTransferParams--><!--Device-usbManager-interface UsbDataTransferParams-End-->

**系统能力：** SystemCapability.USB.USBManager

## 导入模块

```TypeScript
import { usbManager } from '@kit.BasicServicesKit';
import { serialManager } from '@kit.BasicServicesKit';
```

## buffer

```TypeScript
buffer: Uint8Array
```

用于存储读或者写请求时的数据。

**类型：** Uint8Array

**起始版本：** 23

<!--Device-UsbDataTransferParams-buffer: Uint8Array--><!--Device-UsbDataTransferParams-buffer: Uint8Array-End-->

**系统能力：** SystemCapability.USB.USBManager

## callback

```TypeScript
callback: AsyncCallback<SubmitTransferCallback>
```

传输完成时的回调函数，签名：(err: Error, data: SubmitTransferCallback) => void。err为错误对象（成功时为null），data包含传输状态、实际长度等信息。

**类型：** [AsyncCallback](arkts-basicservices-asynccallback-t.md)&lt;[SubmitTransferCallback](arkts-basicservices-usbmanager-submittransfercallback-i.md)&gt;

**起始版本：** 23

<!--Device-UsbDataTransferParams-callback: AsyncCallback<SubmitTransferCallback>--><!--Device-UsbDataTransferParams-callback: AsyncCallback<SubmitTransferCallback>-End-->

**系统能力：** SystemCapability.USB.USBManager

## devPipe

```TypeScript
devPipe: USBDevicePipe
```

用于确定总线地址和设备地址，需要调用[connectDevice](arkts-basicservices-usbmanager-connectdevice-f.md)获取。

**类型：** USBDevicePipe

**起始版本：** 23

<!--Device-UsbDataTransferParams-devPipe: USBDevicePipe--><!--Device-UsbDataTransferParams-devPipe: USBDevicePipe-End-->

**系统能力：** SystemCapability.USB.USBManager

## endpoint

```TypeScript
endpoint: int
```

端点地址，取值范围为[1, 255]的正整数。需要调用[getDevices](arkts-basicservices-usbmanager-getdevices-f.md)获取设备信息，通过endpoint的address属性确定端点信息，通过direction 属性确定端点方向。

**类型：** int

**起始版本：** 23

<!--Device-UsbDataTransferParams-endpoint: int--><!--Device-UsbDataTransferParams-endpoint: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## flags

```TypeScript
flags: UsbTransferFlags
```

USB传输标志，用于控制传输行为。可选值包括：0（将短帧报告为错误）、1（自动释放传输缓冲区）、2（完成回调后自动释放传输资源）、3（传输增加一个额外的数据包）。

**类型：** [UsbTransferFlags](arkts-basicservices-usbmanager-usbtransferflags-e.md)

**起始版本：** 23

<!--Device-UsbDataTransferParams-flags: UsbTransferFlags--><!--Device-UsbDataTransferParams-flags: UsbTransferFlags-End-->

**系统能力：** SystemCapability.USB.USBManager

## isoPacketCount

```TypeScript
isoPacketCount: int
```

实时传输时数据包的数量，仅用于具有实时传输端点的I/O。取值范围为[0, INT_MAX]的非负数，（单位：个）。

**类型：** int

**起始版本：** 23

<!--Device-UsbDataTransferParams-isoPacketCount: int--><!--Device-UsbDataTransferParams-isoPacketCount: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## length

```TypeScript
length: int
```

数据缓冲区的长度，取值范围为[0, INT_MAX]的非负数（期望长度），（单位：字节）。

**类型：** int

**起始版本：** 23

<!--Device-UsbDataTransferParams-length: int--><!--Device-UsbDataTransferParams-length: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## timeout

```TypeScript
timeout: int
```

超时时间（单位：毫秒），指定时间内等待传输完成，若在指定时间内传输完成则正常返回否则返回超时。设置为0时无限等待直到传输完成。传入负数时抛出参数错误异常。

**类型：** int

**起始版本：** 23

<!--Device-UsbDataTransferParams-timeout: int--><!--Device-UsbDataTransferParams-timeout: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## type

```TypeScript
type: UsbEndpointTransferType
```

传输类型，指定USB传输的方式。可选值包括：0x1（实时传输，适合音视频等实时数据流）、0x2（批量传输，适合大量数据非实时传输）、0x3（中断传输，适合小数据量实时传输）。

**类型：** [UsbEndpointTransferType](arkts-basicservices-usbmanager-usbendpointtransfertype-e.md)

**起始版本：** 23

<!--Device-UsbDataTransferParams-type: UsbEndpointTransferType--><!--Device-UsbDataTransferParams-type: UsbEndpointTransferType-End-->

**系统能力：** SystemCapability.USB.USBManager

## userData

```TypeScript
userData: Uint8Array
```

用户上下文数据，用于在回调函数中传递自定义的上下文信息。大小和格式由用户定义，在传输请求中指定，回调中原样返回。

**类型：** Uint8Array

**起始版本：** 23

<!--Device-UsbDataTransferParams-userData: Uint8Array--><!--Device-UsbDataTransferParams-userData: Uint8Array-End-->

**系统能力：** SystemCapability.USB.USBManager

