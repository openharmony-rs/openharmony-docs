# AgentHostProxy

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1630992de2f5af1dcca3ca27d11e23e0321182c9 translatedAt=2026-05-30T07:46:15.837Z pushedAt=2026-05-30T08:00:17.865Z -->

AgentHostProxy is used to send data or security authentication requests from the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) server to the client.

> **NOTE**
>
>  - The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>  - The APIs of this module can be used only in the stage model.
>  - The APIs of this module need to be used in the main thread, and are not supported in sub-threads such as Worker and TaskPool.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## AgentHostProxy

### sendData

sendData(data: string): void

Sends data from the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) server to the client.

**Atomic Service API**: This API can be used in atomic services since API version 24.

**System Capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Parameter Name | Type   | Mandatory | Description |
| ------ | ------ | ---- | ---- |
| data   | string | Yes  | Data to be sent to the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) client. |

**Error Codes:**

For details about the following error codes, refer to [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error Code ID | Error Message                     |
| -------- | ----------------------------|
| 35600002 | Failed to send the IPC message.  |

**Example:**

```ts
import { common, AgentExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[AgentExtensionAbility] ';

export default class MyAgentExtensionAbility extends AgentExtensionAbility {
  // Data sending processing
  onData(proxy: common.AgentHostProxy, data: string) {
    console.info(TAG + `onData ${data}`);
    try {
      // Sends data to the client of AgentExtensionAbility
      proxy.sendData('Hello Client');
    } catch (err) {
      let code = (err as BusinessError).code;
      let msg = (err as BusinessError).message;
      console.error(`${TAG} sendData failed, err code: ${code}, err msg: ${msg}.`);
    }
  }
}
```

### authorize

authorize(handshakeData: string): void

Sends a security authentication request from the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) server to the client.

**Atomic Service API**: This API can be used in atomic services since API version 24.

**System Capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters**

| Parameter Name | Type   | Mandatory | Description |
| -------------- | ------ | --------- | ----------- |
| handshakeData | string | Yes       | Security authentication data to be sent to the client. |

**Error Codes:**

For details about the following error codes, refer to [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error Code ID | Error Message                     |
| -------- | ----------------------------|
| 35600002 | Failed to send the IPC message. |

**Example:**

```ts
import { common, AgentExtensionAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const TAG: string = '[AgentExtensionAbility] ';

export default class MyAgentExtensionAbility extends AgentExtensionAbility {
  // Data sending process
  onAuth(proxy: common.AgentHostProxy, handshakeData: string) {
    console.info(TAG + `onAuth ${handshakeData}`);
    try {
      // Sends authentication data to the client of AgentExtensionAbility
      proxy.authorize('handshake_token');
    } catch (err) {
      let code = (err as BusinessError).code;
      let msg = (err as BusinessError).message;
      console.error(`${TAG} authorize failed, err code: ${code}, err msg: ${msg}.`);
    }
  }
}
```