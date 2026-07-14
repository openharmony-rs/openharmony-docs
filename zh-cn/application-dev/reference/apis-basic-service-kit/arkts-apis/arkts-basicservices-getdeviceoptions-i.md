# GetDeviceOptions

定义设备信息获取的参数选项。

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**类型：** () => void

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

接口调用失败的回调函数。 code为失败返回的错误码。

code:200，表示返回结果中存在无法获得的信息。

**类型：** (data: any, code: number) => void

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## success

```TypeScript
success?: (data: DeviceResponse) => void
```

接口调用成功的回调函数。 data为成功返回的设备信息，具体参考[DeviceResponse](arkts-basicservices-deviceresponse-i.md)。

**类型：** (data: DeviceResponse) => void

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

