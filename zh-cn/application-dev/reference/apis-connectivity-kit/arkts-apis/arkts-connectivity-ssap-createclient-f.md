# createClient

## createClient

```TypeScript
function createClient(address: string): Client
```

创建SSAP客户端实例。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ssap-function createClient(address: string): Client--><!--Device-ssap-function createClient(address: string): Client-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string | 是 | 服务端的设备地址。例如，“11:22:33:AA:BB:FF” &lt;br&gt;长度必须为17，由16进制数字和冒号组成，形如 "11:22:33:AA:BB:FF"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Client](arkts-connectivity-ssap-client-i.md) | Returns a SSAP client instance { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [36100041](../errorcode-nearlink-service.md#36100041-无效地址) | Invalid address. |

