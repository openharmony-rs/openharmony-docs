# getAgentCardByAgentId（系统接口）

## 导入模块

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## getAgentCardByAgentId

```TypeScript
function getAgentCardByAgentId(bundleName: string, agentId: string): Promise<AgentCard>
```

获取指定应用agentId对应的AgentCard。使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.GET_AGENT_CARD

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | AgentCard所属的bundle名称。 |
| agentId | string | 是 | AgentCard所属的agentId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AgentCard](arkts-ability-agentcard-i.md)&gt; | Promise对象，返回指定的AgentCard。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| [18500001](../errorcode-ability.md#18500001-指定的包名无效) | The bundle does not exist or no patch has been applied. |
| [35600001](../errorcode-ability.md#35600001-指定的agentid不存在) | The specified agentId does not exist. |
