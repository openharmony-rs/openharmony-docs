# updateAgentCard（系统接口）

## 导入模块

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## updateAgentCard

```TypeScript
function updateAgentCard(agentCard: AgentCard): Promise<void>
```

更新系统中已存在的AgentCard信息，当[SemVer版本](https://semver.org/)不低于当前已存在的AgentCard时执行覆盖更新。当SemVer版本相同时，系统优先保存通过[registerAgentCard](arkts-ability-agentmanager-registeragentcard-f-sys.md)或[updateAgentCard](arkts-ability-agentmanager-updateagentcard-f-sys.md)接口调用时传入的AgentCard。

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
| agentCard | [AgentCard](arkts-ability-agentcard-i.md) | 是 | 要更新的AgentCard信息。 |

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
| [35600001](../errorcode-ability.md#35600001-指定的agentid不存在) | The specified agentId does not exist. |
| [35600004](../errorcode-ability.md#35600004-指定的agentcard版本低于当前版本) | The specified AgentCard version is older than the current version. |
| [35600005](../errorcode-ability.md#35600005-指定的agentcard版本无效) | The specified AgentCard version is invalid. |
