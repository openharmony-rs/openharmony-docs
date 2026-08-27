# getAddressesByName

## 导入模块

```TypeScript
```

## getAddressesByName

```TypeScript
function getAddressesByName(host: string, callback: AsyncCallback<Array<NetAddress>>): void
```

使用当前默认网络解析主机名以获取所有IP地址。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 需要解析的主机名。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;NetAddress&gt;&gt; | 是 | 回调函数。当使用默认网络解析主机名成功获取所有IP地址，error为undefined，data为获取到的所有IP地址； 否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getAddressesByName("xxxx", (error: BusinessError, data: connection.NetAddress[]) => {
  if (error) {
    console.error(`Failed to get addresses. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let host = "www.example.com";
  netHandle.getAddressesByName(host, (error: BusinessError, data: connection.NetAddress[]) => {
    if (error) {
      console.error(`Failed to get addresses. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```


## getAddressesByName

```TypeScript
function getAddressesByName(host: string): Promise<Array<NetAddress>>
```

使用当前默认网络解析主机名以获取所有IP地址。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.INTERNET

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 需要解析的主机名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;NetAddress & gt; & gt; | Promise对象。返回所有IP地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getAddressesByName("xxxx").then((data: connection.NetAddress[]) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let host = "www.example.com";
  netHandle.getAddressesByName(host).then((data: connection.NetAddress[]) => {
    console.info("Succeeded to get data: " + JSON.stringify(data));
  });
});
```
