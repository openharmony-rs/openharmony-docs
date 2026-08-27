# createVpnConnection

## 导入模块

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## createVpnConnection

```TypeScript
function createVpnConnection(context: VpnExtensionContext): VpnConnection
```

创建一个三方VPN连接对象。

> **说明：**
> 
> 调用createVpnConnection接口前，需要先调用startVpnExtensionAbility接口启用VPN功能。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | VpnExtensionContext | 是 | 指定 context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| VpnConnection | 返回一个VPN连接对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
