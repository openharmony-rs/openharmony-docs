# getNetCapabilitiesSync

## 导入模块

```TypeScript
```

## getNetCapabilitiesSync

```TypeScript
function getNetCapabilitiesSync(netHandle: NetHandle): NetCapabilities
```

获取netHandle对应网络的能力信息，包含上/下行带宽、网络具体能力、网络类型。使用同步方式返回。

**起始版本：** 10

**需要权限：** ohos.permission.GET_NETWORK_INFO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NetCapabilities](arkts-network-connection-netcapabilities-i.md) | 返回网络的能力集。 |

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

  let getNetCapabilitiesSync = connection.getNetCapabilitiesSync(netHandle);
  console.info("Succeeded to get net capabilities sync: " + JSON.stringify(getNetCapabilitiesSync));
});
```
