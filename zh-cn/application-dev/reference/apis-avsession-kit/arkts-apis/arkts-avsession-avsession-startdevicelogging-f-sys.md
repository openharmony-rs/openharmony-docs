# startDeviceLogging（系统接口）

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## startDeviceLogging

```TypeScript
function startDeviceLogging(url: string, maxSize?: number): Promise<void>
```

开始将设备日志写入文件。结果通过Promise异步回调方式返回。

**起始版本：** 13

<!--Device-avSession-function startDeviceLogging(url: string, maxSize?: int): Promise<void>--><!--Device-avSession-function startDeviceLogging(url: string, maxSize?: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 目标文件描述符（打开文件的唯一标识）。 |
| maxSize | number | 否 | 写入最大日志大小（以kB为单位）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。当设备日志写入文件成功时，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |

**示例：**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

let file = await fileIo.open("filePath");
let url = file.fd.toString();
avSession.startDeviceLogging(url, 2048).then(() => {
  console.info('Succeeded in starting device logging.');
})

```

