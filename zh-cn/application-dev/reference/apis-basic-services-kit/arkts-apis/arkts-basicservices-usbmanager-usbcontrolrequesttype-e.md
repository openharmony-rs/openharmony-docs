# USBControlRequestType

控制请求类型，用于指定具体的USB控制请求命令（如获取描述符、设置地址等）。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## USB_REQUEST_TYPE_STANDARD

```TypeScript
USB_REQUEST_TYPE_STANDARD = 0
```

标准请求类型，用于发送USB协议定义的标准控制请求（如设备描述符、设置地址、设置配置等）。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## USB_REQUEST_TYPE_CLASS

```TypeScript
USB_REQUEST_TYPE_CLASS = 1
```

类请求类型，用于发送特定设备类定义的控制请求（如HID类、Mass Storage类等特定请求）。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager

## USB_REQUEST_TYPE_VENDOR

```TypeScript
USB_REQUEST_TYPE_VENDOR = 2
```

厂商请求类型，用于发送厂商自定义的控制请求，具体请求内容由设备厂商定义。

**起始版本：** 9

**系统能力：** SystemCapability.USB.USBManager
