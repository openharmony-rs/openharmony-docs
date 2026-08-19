# getNetExtAttributeSync

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getNetExtAttributeSync

```TypeScript
function getNetExtAttributeSync(netHandle: NetHandle): string
```

获取netHandle对应网络的扩展属性，以确定网络的安全级别。使用同步方式返回。

**起始版本：** 20

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-connection-function getNetExtAttributeSync(netHandle: NetHandle): string--><!--Device-connection-function getNetExtAttributeSync(netHandle: NetHandle): string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 以同步方式返回的网络扩展属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netHandle = connection.getDefaultNetSync();
if (netHandle.netId != 0) {
  let netExtAttribute: string = connection.getNetExtAttributeSync(netHandle);
  console.info("Succeeded to getNetExtAttribute: " + netExtAttribute);
}
```

