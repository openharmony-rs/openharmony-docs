# @ohos.app.agent.agentManager (Agent管理)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

agentManager模块提供Agent管理能力，支持AgentExtensionAbility的连接、断开连接等操作，同时提供与系统中的Agent进行交互的能力，例如获取设备上的AgentCard信息。

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

## agentManager.connectAgentExtensionAbility
 	 
connectAgentExtensionAbility(want: Want, agentId: string, callback: AgentExtensionConnectCallback): Promise\<AgentProxy>
 	 
将当前调用方组件连接到[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)。通过返回的[AgentProxy](js-apis-inner-application-agentProxy.md)与[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)进行通信，以使用AgentExtensionAbility对外提供的能力。
 	 
**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CONNECT_AGENT

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名   | 类型                                  | 必填 | 说明           |
| -------- | ------------------------------------- | ---- | ------------ |
| want     | [Want](js-apis-app-ability-want.md)   | 是   | [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)所属的Want信息，通常需要包括bundle名称、ability名称。 |
| agentId  | string                                | 是   | [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)所属的agentId。 |
| callback | [AgentExtensionConnectCallback](js-apis-inner-application-agentExtensionConnectCallback.md) | 是   | 连接回调函数，包含接收[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)服务端的数据、安全认证数据以及断开连接事件的回调接口。 |
 	 
**返回值：**
 	 
| 类型                       | 说明                         |
| -------------------------- | ---------------------------- |
| Promise\<[AgentProxy](js-apis-inner-application-agentProxy.md)> | Promise对象，返回的AgentProxy对象，用于从客户端向AgentExtensionAbility服务端发送数据或安全认证请求。 |
 	 
**错误码：**
 	 
以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201      | Permission denied. |
| 202      | Not system application. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000008 | The crowdtesting application expires. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed. 2.System service fled to communicate with dependency module. |
| 16000053 | The ability is not on the top of the UI. |
| 16000073 | The app clone index is invalid. |
| 35600001 | The specified agentId does not exist. |
| 35600003 | Maximum connections from the same caller have been reached. |

**示例：**

```ts
import { common, Want, agentManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  comProxy: common.AgentProxy | null = null;
  connectCallback: common.AgentExtensionConnectCallback = {
    onData: (data: string) => {
      console.info(`onData, data: ${data}.`);
    },
    onAuth: (handShakeData: string): void => {
      console.info(`onData, data: ${handShakeData}.`);
    },
    onDisconnect: () => {
      console.info(`onDisconnect.`);
      this.comProxy = null;
    }
  }
  build() {
    Column() {
      Row() {
        // 创建连接按钮
        Button('connect ability')
          .enabled(true)
          .onClick(() => {
            let connectWant: Want = {
              bundleName: 'com.acts.agentextensionability',
              abilityName: 'AgentExtAbility',
            };
            let agentId: string = 'test';
            try {
              // 连接AgentExtensionAbility
              agentManager.connectAgentExtensionAbility(connectWant, agentId, this.connectCallback)
                .then((proxy: common.AgentProxy) => {
                  this.comProxy = proxy;
                })
                .catch((err: BusinessError) => {
                  console.error(`connectAgentExtensionAbility failed, err code: ${err.code}, err msg: ${err.message}.`);
                });
            } catch (err) {
              let code = (err as BusinessError).code;
              let msg = (err as BusinessError).message;
              console.error(`connectAgentExtensionAbility failed, err code: ${code}, err msg: ${msg}.`);
            }
          })
      }
    }
  }
}
```

## agentManager.disconnectAgentExtensionAbility
 	 
disconnectAgentExtensionAbility(proxy: AgentProxy): Promise\<void>

断开与指定proxy的[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)的连接。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.CONNECT_AGENT

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型                                             | 必填 | 说明           |
| ------ | ------------------------------------------------ | ---- | ------------ |
| proxy  | [AgentProxy](js-apis-inner-application-agentProxy.md) | 是   | 要断开连接的[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)对应的Proxy对象，在调用[connectAgentExtensionAbility](#agentmanagerconnectagentextensionability)接口连接[AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md)时会返回其对应的proxy对象。 |

**返回值：**

| 类型            | 说明            |
| --------------- | --------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[元能力子系统错误码](errorcode-ability.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201      | Permission denied. |
| 202      | Not system application. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
 	 
**示例：**

```ts
import { common, Want, agentManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
@Entry
@Component
struct Index {
  comProxy: common.AgentProxy | null = null;
  build() {
    Column() {
      Row() {
        // 创建连接按钮
        Button('connect ability')
          .enabled(true)
          .onClick(() => {
            try {
              // 连接AgentExtensionAbility
              agentManager.disconnectAgentExtensionAbility(this.comProxy)
                .then(() => {
                })
                .catch((err: BusinessError) => {
                  console.error(`connectAgentExtensionAbility failed, err code: ${err.code}, errmsg: ${err.message}.`);
                });
            } catch (err) {
              let code = (err as BusinessError).code;
              let msg = (err as BusinessError).message;
              console.error(`connectAgentExtensionAbility failed, err code: ${code}, err msg ${msg}.`);
            }
          })
      }
    }
  }
}
```