# @ohos.app.agent.agentManager (Agent Management) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

The agentManager module provides the agent management capability, including connecting to and disconnecting from AgentExtensionAbility. It also provides the capability to interact with agents in the system, for example, obtaining AgentCard information from a device.

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { agentManager } from '@kit.AbilityKit';
```

## agentManager.getAllAgentCards

getAllAgentCards(): Promise\<Array\<AgentCard>>

Obtains all AgentCards on the device. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permission**: ohos.permission.GET_AGENT_CARD

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**System API**: This is a system API.

**Return value:**

| Type| Description|
| -------- | -------- |
| Promise<Array<[AgentCard](./js-apis-inner-application-AgentCard.md#agentcard-1)>> | Promise used to return all AgentCard arrays on the device.|

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |

**Example:**

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

Obtains all AgentCards of a specified application. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permission**: ohos.permission.GET_AGENT_CARD

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Name of the bundle to which the AgentCard belongs.|

**Return value:**

| Type| Description|
| -------- | -------- |
| Promise<Array<[AgentCard](./js-apis-inner-application-AgentCard.md#agentcard-1)>> | Promise used to return all AgentCard arrays in the specified bundleName.|

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| 18500001 | The bundle does not exist or no patch has been applied. |

**Example:**

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

Obtains the AgentCard corresponding to the agent ID of a specified application. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permission**: ohos.permission.GET_AGENT_CARD

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Name of the bundle to which the AgentCard belongs.|
| agentId | string | Yes| ID of the agent to which the AgentCard belongs.|

**Return value:**

| Type| Description|
| -------- | -------- |
| Promise<[AgentCard](./js-apis-inner-application-AgentCard.md#agentcard-1)> | Promise used to return the specified AgentCard.|

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| 18500001 | The bundle does not exist or no patch has been applied. |
| 35600001 | The specified agentId does not exist. |

**Example:**

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

Connects the current caller component to the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md). Communicates with the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) through the returned [AgentProxy](js-apis-inner-application-agentProxy-sys.md) to use the capabilities provided by the AgentExtensionAbility.

**System API**: This is a system API.

**Required permission**: ohos.permission.CONNECT_AGENT

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters**

| Name  | Type                                 | Mandatory| Description          |
| -------- | ------------------------------------- | ---- | ------------ |
| want     | [Want](js-apis-app-ability-want.md)   | Yes  | Want information to which the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) belongs, including the bundle name and ability name.|
| agentId  | string                                | Yes  | ID of the agent to which the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) belongs.|
| callback | [AgentExtensionConnectCallback](js-apis-inner-application-agentExtensionConnectCallback-sys.md) | Yes  | Connection callback, containing callback APIs for receiving data from the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) server, security authentication data, and disconnection events.|

**Return value:**

| Type                      | Description                        |
| -------------------------- | ---------------------------- |
| Promise\<[AgentProxy](js-apis-inner-application-agentProxy-sys.md)> | Promise used to return the AgentProxy object, which is used to send data or security authentication requests from the client to the AgentExtensionAbility server.|

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error Code| Error Message|
| -------- | -------- |
| 201      | Permission denied. |
| 202      | Not system application. |
| 16000001 | The specified ability does not exist. |
| 16000002 | Incorrect ability type. |
| 16000004 | Cannot start an invisible component. |
| 16000005 | The specified process does not have the permission. |
| 16000008 | The crowdtesting application expires. |
| 16000012 | The application is controlled. |
| 16000013 | The application is controlled by enterprise device management (EDM). |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |
| 16000053 | The ability is not on the top of the UI. |
| 16000073 | The app clone index is invalid. |
| 35600001 | The specified agentId does not exist. |
| 35600003 | Maximum connections from the same caller have been reached. Please disconnect at least one agent extension beforehand.|

**Example:**

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
        // Create a connection button.
        Button('connect ability')
          .enabled(true)
          .onClick(() => {
            let connectWant: Want = {
              bundleName: 'com.acts.agentextensionability',
              abilityName: 'AgentExtAbility',
            };
            let agentId: string = 'test';
            try {
              // Connect to AgentExtensionAbility.
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

Disconnects from the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) of a specified proxy.

**System API**: This is a system API.

**Required permission**: ohos.permission.CONNECT_AGENT

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters**

| Name| Type                                            | Mandatory| Description          |
| ------ | ------------------------------------------------ | ---- | ------------ |
| proxy  | [AgentProxy](js-apis-inner-application-agentProxy-sys.md) | Yes  | Proxy object corresponding to the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) to be disconnected. When the [connectAgentExtensionAbility](#agentmanagerconnectagentextensionability) API is called to connect to the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md), the corresponding proxy object is returned.|

**Return value:**

| Type           | Description           |
| --------------- | --------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error Code| Error Message|
| -------- | -------- |
| 201      | Permission denied. |
| 202      | Not system application. |
| 16000050 | Internal error. Possible causes: 1.Connect to system service failed. 2.System service failed to communicate with dependency module. |

**Example:**

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
        // Create a connection button.
        Button('connect ability')
          .enabled(true)
          .onClick(() => {
            try {
              // Connect to AgentExtensionAbility.
              agentManager.disconnectAgentExtensionAbility(this.comProxy)
                .then(() => {
                })
                .catch((err: BusinessError) => {
                  console.error(`connectAgentExtensionAbility failed, error code: ${err.code}, error msg: ${err.message}.`);
                });
            } catch (err) {
              let code = (err as BusinessError).code;
              let msg = (err as BusinessError).message;
              console.error(`connectAgentExtensionAbility failed, error code: ${code}, error msg: ${msg}.`);
            }
          })
      }
    }
  }
}
```
