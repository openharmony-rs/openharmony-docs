# getConnectionPropertiesSync

## 导入模块

```TypeScript
```

## getConnectionPropertiesSync

```TypeScript
function getConnectionPropertiesSync(netHandle: NetHandle): ConnectionProperties
```

获取netHandle对应的网络的连接信息，包含网卡名称、域名、链路信息、路由信息、网络地址及最大传输单元。使用同步方式返回。

**起始版本：** 10

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ConnectionProperties](arkts-network-connection-connectionproperties-i.md) | 返回网络的连接信息。 |

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

connection.getDefaultNet().then((netHandle: connection.NetHandle) => {
  if (netHandle.netId == 0) {
    // 当前没有已连接的网络时，netHandle的netId为0，属于异常场景。可根据实际情况添加处理机制。
    return;
  }
  let connectionproperties = connection.getConnectionPropertiesSync(netHandle);
  console.info("Succeeded to get connectionproperties: " + JSON.stringify(connectionproperties));
});
```
