# getSysVpnConfigList（系统接口）

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## getSysVpnConfigList

```TypeScript
function getSysVpnConfigList(): Promise<Array<SysVpnConfig>>
```

获取所有系统VPN网络配置。

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_VPN

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[SysVpnConfig](arkts-network-vpn-sysvpnconfig-i-sys.md)&gt;&gt; | The promise returned by the all VPN network configuration. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
