# deleteSysVpnConfig（系统接口）

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
import { vpnExtension } from '@kit.NetworkKit';
```

## deleteSysVpnConfig

```TypeScript
function deleteSysVpnConfig(vpnId: string): Promise<void>
```

删除指定vpnId的系统VPN网络配置。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_VPN

<!--Device-vpn-function deleteSysVpnConfig(vpnId: string): Promise<void>--><!--Device-vpn-function deleteSysVpnConfig(vpnId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vpnId | string | 是 | Indicates the uuid of the VPN network configuration. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

