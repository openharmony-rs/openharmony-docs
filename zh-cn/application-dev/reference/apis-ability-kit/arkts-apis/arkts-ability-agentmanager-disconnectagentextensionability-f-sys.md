# disconnectAgentExtensionAbility（系统接口）

## 导入模块

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## disconnectAgentExtensionAbility

```TypeScript
function disconnectAgentExtensionAbility(proxy: AgentProxy): Promise<void>
```

断开与指定proxy的[AgentExtensionAbility](../../../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md)的连接。

**起始版本：** 24

**需要权限：** ohos.permission.CONNECT_AGENT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| proxy | [AgentProxy](arkts-ability-agentproxy-i-sys.md) | 是 | 要断开连接的[AgentExtensionAbility](../../../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md)对应的Proxy对象，在调用[connectAgentExtensionAbility](arkts-ability-agentmanager-connectagentextensionability-f-sys.md)接口连接[AgentExtensionAbility](../../../reference/apis-ability-kit/js-apis-app-agent-agentExtensionAbility.md)时会返回其对应的proxy对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
