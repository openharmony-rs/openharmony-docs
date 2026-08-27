# getDefaultHttpProxy

## 导入模块

```TypeScript
```

## getDefaultHttpProxy

```TypeScript
function getDefaultHttpProxy(callback: AsyncCallback<HttpProxy>): void
```

获取网络的默认代理配置信息。使用callback异步回调。

> **说明：**
> 
> - 如果设置了全局代理，则返回全局代理配置信息。
> 
> - 如果进程使用[setAppNet](arkts-network-connection-setappnet-f.md)绑定到指定[NetHandle](arkts-network-connection-nethandle-i.md)对应的网络，则返回
> [NetHandle](arkts-network-connection-nethandle-i.md)对应网络的代理配置信息。在其它情况下，将返回默认网络的代理配置信息。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;HttpProxy&gt; | 是 | 回调函数。当成功获取网络的默认代理配置信息时，error为undefined，data为网络的默认代理配置信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultHttpProxy((error: BusinessError, data: connection.HttpProxy) => {
  if (error) {
    console.error(`Failed to get default http proxy. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data" + JSON.stringify(data));
});
```


## getDefaultHttpProxy

```TypeScript
function getDefaultHttpProxy(): Promise<HttpProxy>
```

获取网络默认的代理配置信息。使用Promise异步回调。

> **说明：**
> 
> - 如果设置了全局代理，则返回全局代理配置信息。
> 
> - 如果进程使用[setAppNet](arkts-network-connection-setappnet-f.md)绑定到指定[NetHandle](arkts-network-connection-nethandle-i.md)对应的网络，则返回
> [NetHandle](arkts-network-connection-nethandle-i.md)对应网络的代理配置信息。在其它情况下，将返回默认网络的代理配置信息。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;HttpProxy & gt; | 以Promise形式返回网络默认的代理配置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultHttpProxy().then((data: connection.HttpProxy) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error(`Failed to get request. Code:${error.code}, message:${error.message} `);
});
```
