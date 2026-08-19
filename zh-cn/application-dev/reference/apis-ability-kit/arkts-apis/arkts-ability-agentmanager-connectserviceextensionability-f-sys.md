# connectServiceExtensionAbility（系统接口）

## 导入模块

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## connectServiceExtensionAbility

```TypeScript
function connectServiceExtensionAbility(context: AgentExtensionContext, want: Want, callback: ConnectOptions): long
```

将AgentExtensionAbility连接到ServiceExtensionAbility。若目标ServiceExtensionAbility可见，可直接连接；若不可见，需申请 `ohos.permission.START_INVISIBLE_ABILITY`权限；若目标ServiceExtensionAbility位于远程设备上，需申请 `ohos.permission.DISTRIBUTED_DATASYNC`权限。 > **说明：** > > 该接口不支持在多线程和子进程中调用。在多线程中调用将引发CppCrash；在子进程中调用将返回16000050错误码。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-agentManager-function connectServiceExtensionAbility(context: AgentExtensionContext, want: Want, callback: ConnectOptions): long--><!--Device-agentManager-function connectServiceExtensionAbility(context: AgentExtensionContext, want: Want, callback: ConnectOptions): long-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [AgentExtensionContext](arkts-ability-agentextensioncontext-c.md) | 是 | 当前Agent扩展能力的上下文，包含AgentCard信息。 |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 目标ServiceExtensionAbility的Want信息，包含bundleName、abilityName等。 |
| callback | [ConnectOptions](arkts-ability-connectoptions-connectoptions-i.md) | 是 | ConnectOptions类型的回调函数，返回服务连接成功、连接失败、断开的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回一个连接ID，用于标识当前AgentExtensionAbility与ServiceExtensionAbility之间的连接。该连接ID可用于后续调用 [disconnectServiceExtensionAbility]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000053](../errorcode-ability.md#16000053-非顶层ability) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-免安装超时) | Installation-free timed out. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000012](../errorcode-ability.md#16000012-应用被管控) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by enterprise device management (EDM). |
| [16000008](../errorcode-ability.md#16000008-众测应用到期) | The crowdtesting application expires. |
| [16000073](../errorcode-ability.md#16000073-传入的appcloneindex是一个无效值) | The app clone index is invalid. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

