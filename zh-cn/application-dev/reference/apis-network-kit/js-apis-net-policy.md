# @ohos.net.policy (网络策略管理)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

本模块提供网络策略管理能力，采用防火墙技术对用户使用数据流量进行控制管理。

> **说明：**
>
> 本模块首批接口从 API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```ts
import { policy } from '@kit.NetworkKit';
```

## NetBearType

type NetBearType = connection.NetBearType

网络类型。

**系统能力**：SystemCapability.Communication.NetManager.Core

| 类型   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| [connection.NetBearType](./js-apis-net-connection.md#netbeartype) | 网络类型。 |

## policy.showAppNetPolicySettings<sup>22+</sup>

showAppNetPolicySettings(context: Context): Promise\<void>

当需要设置当前应用能否使用Wi-Fi/蜂窝联网时，调用该接口可以打开当前应用的联网设置界面，以设置应用的联网权限。使用Promise异步回调。

**系统能力**：SystemCapability.Communication.NetManager.Core

**设备行为差异**：该接口在Phone、2in1、Tablet设备中可正常调用，在其他设备调用不生效。


**参数：**

| 参数名 | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| context    | [Context](../apis-ability-kit/js-apis-inner-application-context.md) | 是   | Stage模型的应用上下文（仅支持UIAbilityContext和ExtensionContext）。 |

**返回值：**

| 类型                                                    | 说明                          |
| ------------------------------------------------------- | ----------------------------- |
| Promise\<void>  |Promise对象。无返回结果的Promise对象。|

**示例：**

```ts
import { policy } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

const context: common.UIAbilityContext = getContext() as common.UIAbilityContext;
policy.showAppNetPolicySettings(context).then(() => {
    console.info("showAppNetPolicySettings success");
}).catch(() => {
    console.error("showAppNetPolicySettings failed");
    }
)
```

