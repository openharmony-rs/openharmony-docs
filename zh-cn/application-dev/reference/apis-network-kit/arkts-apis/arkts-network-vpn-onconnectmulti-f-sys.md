# on_connectMulti（系统接口）

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
import { vpnExtension } from '@kit.NetworkKit';
```

## on('connectMulti')

```TypeScript
function on(type: 'connectMulti', callback: Callback<MultiVpnConnectState>): void
```

订阅VPN连接状态变化事件。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_VPN

<!--Device-vpn-function on(type: 'connectMulti', callback: Callback<MultiVpnConnectState>): void--><!--Device-vpn-function on(type: 'connectMulti', callback: Callback<MultiVpnConnectState>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connectMulti' | 是 | Indicates multi vpn connect state changes. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;MultiVpnConnectState&gt; | 是 | The callback of the multi vpn connect state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [19900002](../errorcode-net-vpn.md#19900002-系统内部错误) | System internal error. |
| [19900001](../errorcode-net-vpn.md#19900001-无效参数) | Invalid parameter value. |

