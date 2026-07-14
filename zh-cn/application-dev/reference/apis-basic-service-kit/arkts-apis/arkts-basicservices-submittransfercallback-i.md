# SubmitTransferCallback

Usb异步传输回调。

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## actualLength

```TypeScript
actualLength: number
```

读写操作的实际长度值。（单位：字节）。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## isoPacketDescs

```TypeScript
isoPacketDescs: Array<Readonly<UsbIsoPacketDescriptor>>
```

实时传输的分包信息。

**类型：** Array<Readonly<UsbIsoPacketDescriptor>>

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

## status

```TypeScript
status: UsbTransferStatus
```

读写操作完成的状态。

**类型：** UsbTransferStatus

**起始版本：** 18

**系统能力：** SystemCapability.USB.USBManager

