# getAppNet

## 导入模块

```TypeScript
```

## getAppNet

```TypeScript
function getAppNet(callback: AsyncCallback<NetHandle>): void
```

获取App绑定的网络句柄。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;NetHandle&gt; | 是 | 回调函数。当成功获取App绑定的网络信息时，error为undefined，data为获取到App绑定的网络信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getAppNet((error: BusinessError, data: connection.NetHandle) => {
  if (error) {
    console.error(`Failed to get App net. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
})
```


## getAppNet

```TypeScript
function getAppNet(): Promise<NetHandle>
```

获取App绑定的网络信息。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;NetHandle & gt; | 以Promise形式返回App绑定的网络信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getAppNet().then((data: connection.NetHandle) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error(`Failed to get request. Code:${error.code}, message:${error.message}`);
});
```
