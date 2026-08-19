# getAllNetsSync

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getAllNetsSync

```TypeScript
function getAllNetsSync(): Array<NetHandle>
```

获取所有处于连接状态的网络列表。使用同步方式返回。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-connection-function getAllNetsSync(): Array<NetHandle>--><!--Device-connection-function getAllNetsSync(): Array<NetHandle>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;NetHandle&gt; | 返回所有处于连接状态的网络列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let netHandle = connection.getAllNetsSync();
```

