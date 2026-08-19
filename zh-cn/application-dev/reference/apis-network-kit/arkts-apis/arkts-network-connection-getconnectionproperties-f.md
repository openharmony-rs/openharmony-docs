# getConnectionProperties

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getConnectionProperties

```TypeScript
function getConnectionProperties(netHandle: NetHandle, callback: AsyncCallback<ConnectionProperties>): void
```

获取netHandle对应的网络的连接信息，包含网卡名称、域名、链路信息、路由信息、网络地址及最大传输单元。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-connection-function getConnectionProperties(netHandle: NetHandle, callback: AsyncCallback<ConnectionProperties>): void--><!--Device-connection-function getConnectionProperties(netHandle: NetHandle, callback: AsyncCallback<ConnectionProperties>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ConnectionProperties](arkts-network-connection-connectionproperties-i.md)&gt; | 是 | 回调函数。当成功获取netHandle对应的网络的连接信息时，error为undefined，data为获取的网络 连接信息；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  connection.getConnectionProperties(netHandle, (error: BusinessError, data: connection.ConnectionProperties) => {
    if (error) {
      console.error(`Failed to get connection properties. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  })
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return 0;
  }
  connection.getConnectionProperties(netHandle, (error: BusinessError|null, data: connection.ConnectionProperties|undefined) => {
    if (error) {
      console.error(`Failed to get connection properties. Code:${error.code}, message:${error.message}`);
      return;
    }
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  })
});
```


## getConnectionProperties

```TypeScript
function getConnectionProperties(netHandle: NetHandle): Promise<ConnectionProperties>
```

获取netHandle对应的网络的连接信息，包含网卡名称、域名、链路信息、路由信息、网络地址及最大传输单元。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-connection-function getConnectionProperties(netHandle: NetHandle): Promise<ConnectionProperties>--><!--Device-connection-function getConnectionProperties(netHandle: NetHandle): Promise<ConnectionProperties>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 数据网络的句柄。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ConnectionProperties](arkts-network-connection-connectionproperties-i.md)&gt; | Promise对象，返回网络的连接信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }

  connection.getConnectionProperties(netHandle).then((data: connection.ConnectionProperties) => {
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  })
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return 0;
  }

  connection.getConnectionProperties(netHandle).then((data: connection.ConnectionProperties) => {
    console.info(`Succeeded to get data: ${JSON.stringify(data)}`);
  })
});
```

