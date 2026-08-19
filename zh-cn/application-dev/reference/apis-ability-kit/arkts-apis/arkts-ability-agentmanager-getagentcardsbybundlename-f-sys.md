# getAgentCardsByBundleName（系统接口）

## 导入模块

```TypeScript
import { agentManager } from '@kit.AbilityKit';
```

## getAgentCardsByBundleName

```TypeScript
function getAgentCardsByBundleName(bundleName: string): Promise<Array<AgentCard>>
```

获取指定应用的所有AgentCard。使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.GET_AGENT_CARD

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-agentManager-function getAgentCardsByBundleName(bundleName: string): Promise<Array<AgentCard>>--><!--Device-agentManager-function getAgentCardsByBundleName(bundleName: string): Promise<Array<AgentCard>>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | AgentCard所属的bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AgentCard](arkts-ability-agentcard-i.md)&gt;&gt; | Promise对象，返回指定bundleName内的所有AgentCard数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [18500001](../errorcode-ability.md#18500001-指定的包名无效) | The bundle does not exist or no patch has been applied. |

