# @ohos.app.agent.agentManager (Agent信息管理)(系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

Agent信息管理提供与系统中的Agent进行交互的能力，包括获取设备上的AgentCard信息。

> **说明：**
>
> 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口均为系统接口。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { agentManager } from '@kit.AbilityKit';
```

## agentManager.getAllAgentCards

getAllAgentCards(): Promise\<Array\<AgentCard>>

获取设备上所有的AgentCard。使用Promise异步回调。

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.GET_AGENT_CARD

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**系统接口**：此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise<Array<[AgentCard](./js-apis-inner-application-AgentCard.md#agentcard-1)>> | Promise对象，返回设备上所有的AgentCard数组。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |

**示例：**

```ts
import { agentManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

agentManager.getAllAgentCards()
  .then((data) => {
    console.info(`GetAllAgentCards success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`GetAllAgentCards failed, error code: ${err.code}, error msg: ${err.message}.`);
  });
```

## agentManager.getAgentCardsByBundleName

getAgentCardsByBundleName(bundleName: string): Promise\<Array\<AgentCard>>

获取指定应用的所有AgentCard。使用Promise异步回调。

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.GET_AGENT_CARD

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| bundleName | string | 是 | AgentCard所属的bundle名称。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise<Array<[AgentCard](./js-apis-inner-application-AgentCard.md#agentcard-1)>> | Promise对象，返回指定bundleName内的所有AgentCard数组。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| 18500001 | The bundle does not exist or no patch has been applied. |

**示例：**

```ts
import { agentManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';

agentManager.getAgentCardsByBundleName(bundleName)
  .then((data) => {
    console.info(`GetAgentCardsByBundleName success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`GetAgentCardsByBundleName failed, error code: ${err.code}, error msg: ${err.message}.`);
  });
```

## agentManager.getAgentCardByAgentId

getAgentCardByAgentId(bundleName: string, agentId: string): Promise\<AgentCard>

获取指定应用agentId对应的AgentCard。使用Promise异步回调。

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.GET_AGENT_CARD

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**系统接口**：此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| bundleName | string | 是 | AgentCard所属的bundle名称。 |
| agentId | string | 是 | AgentCard所属的agentId。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise<[AgentCard](./js-apis-inner-application-AgentCard.md#agentcard-1)> | Promise对象，返回指定的AgentCard。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| 18500001 | The bundle does not exist or no patch has been applied. |
| 35600001 | The specified agentId does not exist. |

**示例：**

```ts
import { agentManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';
let agentId = 'agent_001';

agentManager.getAgentCardByAgentId(bundleName, agentId)
  .then((data) => {
    console.info(`GetAgentCardByAgentId success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`GetAgentCardByAgentId failed, error code: ${err.code}, error msg: ${err.message}.`);
  });
```
