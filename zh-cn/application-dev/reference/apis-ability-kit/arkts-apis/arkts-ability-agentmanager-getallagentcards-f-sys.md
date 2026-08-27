# getAllAgentCards（系统接口）

## 导入模块

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## getAllAgentCards

```TypeScript
function getAllAgentCards(): Promise<Array<AgentCard>>
```

获取设备上所有的AgentCard。使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.GET_AGENT_CARD

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AgentCard](arkts-ability-agentcard-i.md)&gt;&gt; | Promise对象，返回设备上所有的AgentCard数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
