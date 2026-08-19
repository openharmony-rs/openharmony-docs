# isDefaultNetMeteredSync

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## isDefaultNetMeteredSync

```TypeScript
function isDefaultNetMeteredSync(): boolean
```

检查当前网络上的数据流量使用是否被计费（例如：WiFi网络不会被计费，蜂窝网络会被计费）。使用同步方式返回。

**起始版本：** 10

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-connection-function isDefaultNetMeteredSync(): boolean--><!--Device-connection-function isDefaultNetMeteredSync(): boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前网络上的数据流量是否被计费。true表示会被计费，false表示不会被计费。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let isMetered = connection.isDefaultNetMeteredSync();
```

