# createVpnConnection（系统接口）

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## createVpnConnection

```TypeScript
function createVpnConnection(context: AbilityContext): VpnConnection
```

创建一个 VPN 连接对象。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [AbilityContext](arkts-network-vpn-abilitycontext-t.md) | 是 | 指定 context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VpnConnection](arkts-network-vpnextension-vpnconnection-i.md) | 返回一个 VPN 连接对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |

**示例**

```TypeScript
> 说明：
> 
> 在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

Stage 模型示例：
```
