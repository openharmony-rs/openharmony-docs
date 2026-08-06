# UsbDataTransferParams

作为通用USB数据传输接口，客户端需要填充这个对象中的参数，用以发起传输请求。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-usbManager-interface UsbDataTransferParams--><!--Device-usbManager-interface UsbDataTransferParams-End-->

**系统能力：** SystemCapability.USB.USBManager

## buffer

```TypeScript
buffer: Uint8Array
```

用于存储读或者写请求时的数据。

**类型：** Uint8Array

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-UsbDataTransferParams-buffer: Uint8Array--><!--Device-UsbDataTransferParams-buffer: Uint8Array-End-->

**系统能力：** SystemCapability.USB.USBManager

## callback

```TypeScript
callback: AsyncCallback<SubmitTransferCallback>
```

传输完成时的回调信息。

**类型：** AsyncCallback&lt;SubmitTransferCallback&gt;

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-UsbDataTransferParams-callback: AsyncCallback<SubmitTransferCallback>--><!--Device-UsbDataTransferParams-callback: AsyncCallback<SubmitTransferCallback>-End-->

**系统能力：** SystemCapability.USB.USBManager

## devPipe

```TypeScript
devPipe: USBDevicePipe
```

用于确定总线地址和设备地址，需要调用[usbManager.connectDevice]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取。

**类型：** USBDevicePipe

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-UsbDataTransferParams-devPipe: USBDevicePipe--><!--Device-UsbDataTransferParams-devPipe: USBDevicePipe-End-->

**系统能力：** SystemCapability.USB.USBManager

## endpoint

```TypeScript
endpoint: int
```

端点地址，正整数。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-UsbDataTransferParams-endpoint: int--><!--Device-UsbDataTransferParams-endpoint: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## flags

```TypeScript
flags: UsbTransferFlags
```

USB传输标志。

**类型：** UsbTransferFlags

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-UsbDataTransferParams-flags: UsbTransferFlags--><!--Device-UsbDataTransferParams-flags: UsbTransferFlags-End-->

**系统能力：** SystemCapability.USB.USBManager

## isoPacketCount

```TypeScript
isoPacketCount: int
```

实时传输时数据包的数量，仅用于具有实时传输端点的I/O。必须是非负数，（单位：个数）。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-UsbDataTransferParams-isoPacketCount: int--><!--Device-UsbDataTransferParams-isoPacketCount: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## length

```TypeScript
length: int
```

数据缓冲区的长度，必须是非负数（期望长度）。（单位：字节）。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-UsbDataTransferParams-length: int--><!--Device-UsbDataTransferParams-length: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## timeout

```TypeScript
timeout: int
```

超时时间。（单位：毫秒）。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-UsbDataTransferParams-timeout: int--><!--Device-UsbDataTransferParams-timeout: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## type

```TypeScript
type: UsbEndpointTransferType
```

传输类型。

**类型：** UsbEndpointTransferType

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-UsbDataTransferParams-type: UsbEndpointTransferType--><!--Device-UsbDataTransferParams-type: UsbEndpointTransferType-End-->

**系统能力：** SystemCapability.USB.USBManager

## userData

```TypeScript
userData: Uint8Array
```

用户上下文数据。

**类型：** Uint8Array

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-UsbDataTransferParams-userData: Uint8Array--><!--Device-UsbDataTransferParams-userData: Uint8Array-End-->

**系统能力：** SystemCapability.USB.USBManager

