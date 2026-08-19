# setPacUrl

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setPacUrl

```TypeScript
function setPacUrl(pacUrl: string): void
```

设置系统级代理自动配置（Proxy Auto Config，PAC）脚本地址。 > **说明：** > > 只支持设置脚本地址，不支持解析和启用代理功能，如需设置脚本并启用代理，则可调用[setPacFileUrl](arkts-network-connection-setpacfileurl-f.md)接口。

**起始版本：** 15

**需要权限：** ohos.permission.SET_PAC_URL

<!--Device-connection-function setPacUrl(pacUrl: string): void--><!--Device-connection-function setPacUrl(pacUrl: string): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pacUrl | string | 是 | 需要设置的PAC脚本的地址，该接口不会对脚本地址进行校验。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let pacUrl = "xxx";
connection.setPacUrl(pacUrl);
```

