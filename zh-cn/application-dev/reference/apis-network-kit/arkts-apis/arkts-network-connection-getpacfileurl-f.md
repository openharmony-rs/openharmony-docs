# getPacFileUrl

## 导入模块

```TypeScript
```

## getPacFileUrl

```TypeScript
function getPacFileUrl(): string
```

获取当前PAC脚本的URL地址。

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前PAC脚本的URL地址，如果没有PAC脚本则返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let pacFileUrl = connection.getPacFileUrl();
console.info("Succeeded to get pacFileUrl");
```
