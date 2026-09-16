# registerAgentCard（系统接口）

## 导入模块

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## registerAgentCard

```TypeScript
function registerAgentCard(agentCard: AgentCard): Promise<void>
```

注册AgentCard到系统中，使系统能够识别和调用对应的AgentExtensionAbility。

系统会根据类型对appInfo进行校验：

- APP、LOW_CODE类型：校验bundle和ability是否存在，并验证ability是否为agent类型。  
- ATOMIC_SERVICE类型：在原子化服务已安装时，校验ability是否存在，并验证ability是否为agent类型。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MODIFY_AGENT_CARD

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agentCard | [AgentCard](arkts-ability-agentcard-i.md) | 是 | 要注册的AgentCard信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000001](../errorcode-ability.md#16000001-指定的ability名称不存在) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-接口调用ability类型错误) | Incorrect ability type. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| [18500001](../errorcode-ability.md#18500001-指定的包名无效) | The bundle does not exist or no patch has been applied. |
| [35600005](../errorcode-ability.md#35600005-指定的agentcard版本无效) | The specified AgentCard version is invalid. |
| [35600006](../errorcode-ability.md#35600006-指定的agentcard已被注册) | The specified AgentCard has already been registered. Use updateAgentCard instead. |
| [35600008](../errorcode-ability.md#35600008-同一应用下agentcard数量达到了上限) | The number of AgentCards in the bundle reaches the limit. |
