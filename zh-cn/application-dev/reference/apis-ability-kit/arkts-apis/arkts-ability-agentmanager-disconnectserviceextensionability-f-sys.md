# disconnectServiceExtensionAbility（系统接口）

## 导入模块

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## disconnectServiceExtensionAbility

```TypeScript
function disconnectServiceExtensionAbility(context: AgentExtensionContext, connectId: long): Promise<void>
```

断开AgentExtensionAbility与ServiceExtensionAbility的连接。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-agentManager-function disconnectServiceExtensionAbility(context: AgentExtensionContext, connectId: long): Promise<void>--><!--Device-agentManager-function disconnectServiceExtensionAbility(context: AgentExtensionContext, connectId: long): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [AgentExtensionContext](arkts-ability-agentextensioncontext-c.md) | 是 | 当前Agent扩展能力的上下文，包含AgentCard信息。 |
| connectId | long | 是 | [connectServiceExtensionAbility](arkts-ability-agentmanager-connectserviceextensionability-f-sys.md)返回的连 接ID，用于标识要断开的目标连接。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000011](../errorcode-ability.md#16000011-上下文对象不存在) | The context does not exist. |

