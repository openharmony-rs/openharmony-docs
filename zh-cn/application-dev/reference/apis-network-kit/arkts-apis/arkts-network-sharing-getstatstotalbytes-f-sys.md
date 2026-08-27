# getStatsTotalBytes（系统接口）

## 导入模块

```TypeScript
```

## getStatsTotalBytes

```TypeScript
function getStatsTotalBytes(callback: AsyncCallback<number>): void
```

获取共享网络总数据量，使用 callback 异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，number 代表数据量，单位：KB。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

sharing.getStatsTotalBytes((error: BusinessError, data: number) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


## getStatsTotalBytes

```TypeScript
function getStatsTotalBytes(): Promise<number>
```

获取共享网络总数据量，使用 Promise 异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | 以 Promise 形式返回共享网络总数据量，单位：KB。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

sharing
  .getStatsTotalBytes()
  .then((data: number) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```
