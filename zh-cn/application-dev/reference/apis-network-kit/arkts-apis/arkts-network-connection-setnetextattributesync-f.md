# setNetExtAttributeSync

## 导入模块

```TypeScript
```

## setNetExtAttributeSync

```TypeScript
function setNetExtAttributeSync(netHandle: NetHandle, netExtAttribute: string): void
```

为netHandle对应的网络设置扩展属性，标识网络的安全级别。使用同步方式返回。

> **说明：**
> 
> 该接口所需的权限目前仅支持PC设备。

**起始版本：** 20

**需要权限：** ohos.permission.SET_NET_EXT_ATTRIBUTE

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netHandle | NetHandle | 是 | 网络句柄。 |
| netExtAttribute | string | 是 | 需要设置的网络扩展属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let netExtAttribute: string = "xxx";
let netHandle = connection.getDefaultNetSync();
if (netHandle.netId != 0) {
  connection.setNetExtAttributeSync(netHandle, netExtAttribute);
}
```
