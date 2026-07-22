# createPort

## 导入模块

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## createPort

```TypeScript
function createPort(uuid: string): void
```

通过UUID创建可以接收数据的星闪端口。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataTransfer-function createPort(uuid: string): void--><!--Device-dataTransfer-function createPort(uuid: string): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 应用服务UUID<br>长度必须为36，由16进制数字字符和连字符共36个字符组成，形如“FFFFFFFF-1234-5678-ABCD-000000001234”，代表128比特标识。<br>禁止使用星闪标准服务UUID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100020](../errorcode-nearlink.md#36100020-端口重复注册) | The UUID is already registered. |
| [36100021](../errorcode-nearlink.md#36100021-端口注册数量超出上限) | Port exceeds the upper limit. |
| [36100043](../errorcode-nearlink.md#36100043-无效uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

