# hasDefaultNetSync

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## hasDefaultNetSync

```TypeScript
function hasDefaultNetSync(): boolean
```

获取当前是否有可用网络。使用同步方式返回。

**起始版本：** 10

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回当前是否有可用网络。true表示当前有可用网络，false表示当前没有可用网络。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let hasDefaultNet = connection.hasDefaultNetSync();
```
