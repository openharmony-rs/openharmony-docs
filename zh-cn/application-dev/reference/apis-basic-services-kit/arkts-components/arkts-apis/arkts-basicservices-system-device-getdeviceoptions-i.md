# GetDeviceOptions

定义设备信息获取的参数选项。

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## 导入模块

```TypeScript
import { Device, DeviceResponse, GetDeviceOptions } from '@kit.BasicServicesKit';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数，在接口调用完成后（无论成功或失败）执行，适用于需执行清理或收尾工作的场景。不传入时不执行结束回调。

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

接口调用失败的回调函数，在接口调用失败时执行。data为失败时返回的错误信息对象或错误描述字符串，code为失败返回的错误码。

code:200，表示返回结果中存在无法获得的信息。建议设置此回调以处理错误情况。

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | any | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success?: (data: DeviceResponse) => void
```

接口调用成功的回调函数，在接口调用成功时执行。data 为成功返回的设备信息。不传入时无法获取设备信息，建议设置此回调。

**起始版本：** 3

**废弃版本：** 6

**系统能力：** SystemCapability.Startup.SystemInfo.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [DeviceResponse](arkts-basicservices-system-device-deviceresponse-i.md) | 是 |  |
