# replyCustomEapData

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## replyCustomEapData

```TypeScript
function replyCustomEapData(result: CustomResult, data: EapData): void
```

该接口用于通知系统已完成该步定制化处理。 > **说明：**: > > - 若用于处理收EAP数据包(rx)时的callback，传给系统的EAP数据需要剥离服务器添加的定制部分。 > > - 若用于处理发EAP数据包(tx)时的callback，传给系统的EAP数据为经过添加定制部分后的EAP数据。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION

<!--Device-eap-function replyCustomEapData(result: CustomResult, data: EapData): void--><!--Device-eap-function replyCustomEapData(result: CustomResult, data: EapData): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | [CustomResult](arkts-network-eap-customresult-e.md) | 是 | 定制化判定结果。 |
| data | [EapData](arkts-network-eap-eapdata-i.md) | 是 | 经过定制化的EAP数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33200009](../errorcode-net-eap.md#33200009-netmanager进程不存在) | netmanager stop |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [33200099](../errorcode-net-eap.md#33200099-程序内部错误) | internal error |
| [33200004](../errorcode-net-eap.md#33200004-无效的eap结果值) | Invalid result |
| [33200005](../errorcode-net-eap.md#33200005-无效的eap数据长度) | Invalid size of eap data |

