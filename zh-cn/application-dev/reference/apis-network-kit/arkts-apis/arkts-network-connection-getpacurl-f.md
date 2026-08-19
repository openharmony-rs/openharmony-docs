# getPacUrl

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getPacUrl

```TypeScript
function getPacUrl(): string
```

获取系统级代理自动配置（PAC）脚本地址。

**起始版本：** 15

<!--Device-connection-function getPacUrl(): string--><!--Device-connection-function getPacUrl(): string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回PAC脚本地址。PAC脚本不存在时，抛出2100003错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let pacUrl = connection.getPacUrl();
```

