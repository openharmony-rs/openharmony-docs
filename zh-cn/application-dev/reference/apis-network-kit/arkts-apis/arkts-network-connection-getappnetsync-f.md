# getAppNetSync

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getAppNetSync

```TypeScript
function getAppNetSync(): NetHandle
```

获取App绑定的网络信息。使用同步方式返回。

**起始版本：** 10

<!--Device-connection-function getAppNetSync(): NetHandle--><!--Device-connection-function getAppNetSync(): NetHandle-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NetHandle | 返回App绑定的数据网络。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let netHandle = connection.getAppNetSync();
```

