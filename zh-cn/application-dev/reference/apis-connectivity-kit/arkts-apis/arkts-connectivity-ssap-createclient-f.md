# createClient

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## createClient

```TypeScript
function createClient(address: string): Client
```

创建SSAP客户端实例。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ssap-function createClient(address: string): Client--><!--Device-ssap-function createClient(address: string): Client-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string | 是 | 服务端的设备地址。例如，“11:22:33:AA:BB:FF”<br>长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Client](arkts-connectivity-ssap-client-i.md) | Returns a SSAP client instance {@code Client}. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| 36100003 | NearLink disabled. |
| 36100041 | Invalid address. |
| 36100099 | Operation failed. |

