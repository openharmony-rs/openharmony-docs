# getGlobalHttpProxy（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getGlobalHttpProxy

```TypeScript
function getGlobalHttpProxy(callback: AsyncCallback<HttpProxy>): void
```

获取网络的全局代理配置信息，使用callback异步回调。

**起始版本：** 23

<!--Device-connection-function getGlobalHttpProxy(callback: AsyncCallback<HttpProxy>): void--><!--Device-connection-function getGlobalHttpProxy(callback: AsyncCallback<HttpProxy>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;HttpProxy&gt; | 是 | 回调函数。当成功获取网络的全局代理配置信息时，error为undefined，data为网络的全局代理配置信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getGlobalHttpProxy((error: BusinessError, data: connection.HttpProxy) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


## getGlobalHttpProxy

```TypeScript
function getGlobalHttpProxy(): Promise<HttpProxy>
```

获取网络的全局代理配置信息，使用Promise异步回调。

**起始版本：** 23

<!--Device-connection-function getGlobalHttpProxy(): Promise<HttpProxy>--><!--Device-connection-function getGlobalHttpProxy(): Promise<HttpProxy>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HttpProxy&gt; | 以Promise形式返回网络的全局代理配置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getGlobalHttpProxy().then((data: connection.HttpProxy) => {
  console.info(JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

