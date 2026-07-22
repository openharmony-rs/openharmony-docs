# createCdsmClient

## 导入模块

```TypeScript
import { cdsm } from '@kit.ConnectivityKit';
```

## createCdsmClient

```TypeScript
function createCdsmClient(address: string): CdsmClient
```

创建CDSM客户端实例。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-cdsm-function createCdsmClient(address: string): CdsmClient--><!--Device-cdsm-function createCdsmClient(address: string): CdsmClient-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string | 是 | CDSM服务端地址。<br>长度必须为17。取值约束：由十六进制数字和冒号组成，例如：11:22:33:AA:BB:FF。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CdsmClient](arkts-connectivity-cdsm-cdsmclient-i.md) | 返回CDSM客户端实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100041](../errorcode-nearlink.md#36100041-无效地址) | Invalid address. |
| [36100050](../errorcode-nearlink.md#36100050-不支持合作设备集合管理功能) | Coordinated Devices Set Management not supported. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

