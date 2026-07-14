# USBDeviceRequestParams

控制传输参数。

**起始版本：** 12

**系统能力：** SystemCapability.USB.USBManager

## bRequest

```TypeScript
bRequest: number
```

请求类型。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.USB.USBManager

## bmRequestType

```TypeScript
bmRequestType: number
```

请求控制类型。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.USB.USBManager

## data

```TypeScript
data: Uint8Array
```

用于写入或读取的缓冲区。

**类型：** Uint8Array

**起始版本：** 12

**系统能力：** SystemCapability.USB.USBManager

## wIndex

```TypeScript
wIndex: number
```

请求参数value对应的索引值。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.USB.USBManager

## wLength

```TypeScript
wLength: number
```

请求数据的长度。（单位：字节）。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.USB.USBManager

## wValue

```TypeScript
wValue: number
```

请求参数。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.USB.USBManager

