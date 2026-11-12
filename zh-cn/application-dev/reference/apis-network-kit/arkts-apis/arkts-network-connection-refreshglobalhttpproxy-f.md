# refreshGlobalHttpProxy

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## refreshGlobalHttpProxy

```TypeScript
function refreshGlobalHttpProxy(): Promise<HttpProxy>
```

通知系统重新认证全局代理。

> **说明：** 
> 
> 若当前未配置全局代理或代理配置信息有误（例如未正确配置username和password），则会抛出2100003错误码。可通过
> [getDefaultHttpProxy](arkts-network-connection-getdefaulthttpproxy-f.md)接口查询当前代理配置信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.INTERNET

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-connection-function refreshGlobalHttpProxy(): Promise<HttpProxy>--><!--Device-connection-function refreshGlobalHttpProxy(): Promise<HttpProxy>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HttpProxy](arkts-network-connection-httpproxy-i.md)&gt; | Promise对象，返回全局代理配置信息。其中username和password字段固定为空字符串，不返回有效信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.refreshGlobalHttpProxy().then((data: connection.HttpProxy) => {
  console.info(`Succeeded to refresh global http proxy: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`Failed to refresh global http proxy. Code:${error.code}, message:${error.message}`);
});
```
