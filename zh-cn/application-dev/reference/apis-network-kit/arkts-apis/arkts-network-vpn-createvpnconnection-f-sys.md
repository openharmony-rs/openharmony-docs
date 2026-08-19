# createVpnConnection（系统接口）

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
import { vpnExtension } from '@kit.NetworkKit';
```

## createVpnConnection

```TypeScript
function createVpnConnection(context: AbilityContext): VpnConnection
```

创建一个 VPN 连接对象。

**起始版本：** 10

<!--Device-vpn-function createVpnConnection(context: AbilityContext): VpnConnection--><!--Device-vpn-function createVpnConnection(context: AbilityContext): VpnConnection-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [AbilityContext](arkts-network-vpn-abilitycontext-t.md) | 是 | 指定 context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| VpnConnection | 返回一个 VPN 连接对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

Stage 模型示例：

```TypeScript
import { vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);
  functiontest()
  {
    console.info("vpn createVpnConnection: " + JSON.stringify(this.VpnConnection));
  }
  build() {  }
}
```

