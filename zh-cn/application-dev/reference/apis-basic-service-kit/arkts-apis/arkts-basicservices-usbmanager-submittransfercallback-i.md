# SubmitTransferCallback

Usb异步传输回调。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-usbManager-interface SubmitTransferCallback--><!--Device-usbManager-interface SubmitTransferCallback-End-->

**系统能力：** SystemCapability.USB.USBManager

## actualLength

```TypeScript
actualLength: int
```

读写操作的实际长度值。（单位：字节）。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-SubmitTransferCallback-actualLength: int--><!--Device-SubmitTransferCallback-actualLength: int-End-->

**系统能力：** SystemCapability.USB.USBManager

## isoPacketDescs

```TypeScript
isoPacketDescs: Array<Readonly<UsbIsoPacketDescriptor>>
```

实时传输的分包信息。

**类型：** Array&lt;Readonly&lt;UsbIsoPacketDescriptor&gt;&gt;

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-SubmitTransferCallback-isoPacketDescs: Array<Readonly<UsbIsoPacketDescriptor>>--><!--Device-SubmitTransferCallback-isoPacketDescs: Array<Readonly<UsbIsoPacketDescriptor>>-End-->

**系统能力：** SystemCapability.USB.USBManager

## status

```TypeScript
status: UsbTransferStatus
```

读写操作完成的状态。

**类型：** UsbTransferStatus

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-SubmitTransferCallback-status: UsbTransferStatus--><!--Device-SubmitTransferCallback-status: UsbTransferStatus-End-->

**系统能力：** SystemCapability.USB.USBManager

