# getConnectedVpnAppInfo（系统接口）

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## getConnectedVpnAppInfo

```TypeScript
function getConnectedVpnAppInfo(): Promise<Array<string>>
```

获取已连接的VPN应用信息。

**起始版本：** 20

**需要权限：** ohos.permission.MANAGE_VPN

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | The promise returned by the connected VPN App Info. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [19900001](../errorcode-net-vpn.md#19900001-无效参数) | Invalid parameter value. |
| [19900002](../errorcode-net-vpn.md#19900002-系统内部错误) | System internal error. |
