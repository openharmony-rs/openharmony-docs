# @ohos.app.agent.AgentExtensionAbility (Agent Extension Component)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1630992de2f5af1dcca3ca27d11e23e0321182c9 translatedAt=2026-05-30T03:00:47.340Z pushedAt=2026-05-30T07:27:37.602Z -->

AgentExtensionAbility inherits from [ExtensionAbility](js-apis-app-ability-extensionAbility.md) and provides agent extension capabilities, including lifecycle callback interfaces for creating, destroying, connecting, and disconnecting agent services, as well as callback interfaces for receiving data sent by clients and security authentication.

In this document, the provider of the AgentExtensionAbility component is referred to as the server, and the consumer of the AgentExtensionAbility component is referred to as the client.

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs of this module are not supported in [har](../../quick-start/har-package.md) packages.

## Modules to Import

```ts
import { AgentExtensionAbility } from '@kit.AbilityKit';
```

## Lifecycle

**Figure 1** AgentExtensionAbility lifecycle


- **onCreate**

  When an AgentExtensionAbility instance is created, the system triggers this callback. You can execute initialization logic (such as defining variables and loading resources) in this callback.

- **onConnect**

  This callback is triggered when a client successfully connects to the AgentExtensionAbility.

- **onDisconnect**

  This callback is triggered when a client disconnects from the AgentExtensionAbility.

- **onDestroy**

  This callback is triggered when the AgentExtensionAbility is destroyed.

## AgentExtensionAbility

### Attributes

**Atomic service API:** Starting from API version 24, this attribute is supported in atomic services.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| context | [AgentExtensionContext](js-apis-inner-application-agentExtensionContext.md) | No | No | Context of the AgentExtensionAbility, inherited from [ExtensionContext](js-apis-inner-application-extensionContext.md). |

### onCreate

onCreate(want: Want): void

This callback is triggered when the AgentExtensionAbility instance is created. You can implement initialization logic (such as defining variables and loading resources) in this callback.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| parameter name | type | mandatory | description |
| -------- | -------- | -------- | -------- |
| want |  [Want](js-apis-app-ability-want.md) | Yes | [Want](js-apis-app-ability-want.md) type information related to the current AgentExtensionAbility, including the Ability name, Bundle name, etc. |

**Example:**

```ts
import { AgentExtensionAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AppServiceExtAbility]';

export default class AgentExt extends AgentExtensionAbility {
  // Creating an AgentExtensionAbility
  onCreate(want: Want) {
    hilog.info(0x0000, TAG, `onCreate, want: ${want.abilityName}, bundlename: ${want.bundleName}`);
  }
}
```

### onConnect

onConnect(want: Want, proxy: AgentHostProxy): void

This callback is triggered by the system when a client successfully connects to the AgentExtensionAbility.

**Atomic service API:** Starting from API version 24, this API is supported in atomic services.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters**

| parameter name | type | mandatory | description |
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md) | Yes | [Want](js-apis-app-ability-want.md) type information related to the current AgentExtensionAbility, including the Ability name, Bundle name, etc. |
| proxy | [AgentHostProxy](js-apis-inner-application-agentHostProxy.md) | Yes | [AgentHostProxy](js-apis-inner-application-agentHostProxy.md) object used for communication with the client. |


**Example**

```ts
import { AgentExtensionAbility, Want, common} from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AgentExtensionAbility]';

export default class AgentExt extends AgentExtensionAbility {
  onConnect(want: Want, proxy: common.AgentHostProxy){
    hilog.info(0x0000, TAG, `onConnect, want: ${want.abilityName}, bundlename: ${want.bundleName}`);
  }
}
```

### onDisconnect

onDisconnect(want: Want, proxy: AgentHostProxy): void

This callback is triggered when the client disconnects from the AgentExtensionAbility.

**Atomic service API:** Starting from API version 24, this API is supported in atomic services.

**System capability**: SystemCapability.AgentRuntime.Core

**Parameters**

| parameter name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| want |[Want](js-apis-app-ability-want.md)| Yes | [Want](js-apis-app-ability-want.md) type information related to the current AgentExtensionAbility, including the Ability name, Bundle name, etc. |
| proxy |[AgentHostProxy](js-apis-inner-application-agentHostProxy.md)| Yes | [AgentHostProxy](js-apis-inner-application-agentHostProxy.md) object used for communication with the client. |

**Example:**

```ts
import { AgentExtensionAbility, Want, common } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AgentExtensionAbility]';

export default class AgentExt extends AgentExtensionAbility {
  onDisconnect(want: Want, proxy: common.AgentHostProxy) {
    hilog.info(0x0000, TAG, `onDisconnect, want: ${want.abilityName}, bundlename: ${want.bundleName}`);
  }
}
```

### onData

onData(proxy: AgentHostProxy, data: string): void

When the AgentExtensionAbility receives data sent by the client, the system triggers this callback. The server can send data to the client in this callback through [AgentHostProxy.senddata](js-apis-inner-application-agentHostProxy.md#senddata).

**Atomic service API:** Starting from API version 24, this interface is supported in atomic services.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters**

| parameter name | Type | Mandatory | Description |
| -------- | -------- | -------- |  -------- |
| proxy | [AgentHostProxy](js-apis-inner-application-agentHostProxy.md) | Yes | [AgentHostProxy](js-apis-inner-application-agentHostProxy.md) object, used for communication with the client. |
| data | string | Yes | Indicates the received data. |

**Example**

```ts
import { AgentExtensionAbility, common} from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AgentExtensionAbility]';

export default class AgentExt extends AgentExtensionAbility {
  onData(proxy : common.AgentHostProxy, data : string ){
    hilog.info(0x0000, TAG, `onData, data: ${data}`);
  }
}
```

### onAuth

onAuth(proxy: AgentHostProxy, handshakeData: string): void

When the AgentExtensionAbility receives a security authentication request sent by the client, the system triggers this callback. The server can process the received security authentication request in this callback and send a security authentication request to the client through [AgentHostProxy.authorize](js-apis-inner-application-agentHostProxy.md#authorize).

**Atomic service API:** Starting from API version 24, this interface is supported in atomic services.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| parameter name | type | mandatory | description |
| -------- | -------- | -------- | -------- |
| proxy | [AgentHostProxy](js-apis-inner-application-agentHostProxy.md) | Yes | [AgentHostProxy](js-apis-inner-application-agentHostProxy.md) object, used to send security authentication requests to the client. |
| handshakeData | string | Yes | Indicates the received security authentication data. |

**Example:**

```ts
import { AgentExtensionAbility, common} from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AgentExtensionAbility]';

export default class AgentExt extends AgentExtensionAbility {
  onAuth(proxy : common.AgentHostProxy, handshakeData : string ){
    hilog.info(0x0000, TAG, `onAuth, handshakeData: ${handshakeData}`);
  }
}
```

### onDestroy

onDestroy(): void

This callback is triggered by the system when the AgentExtensionAbility is destroyed.

**Atomic service API:** Starting from API version 24, this interface is supported in atomic services.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Example:**

```ts
import { AgentExtensionAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AgentExtensionAbility]';

export default class AgentExt extends AgentExtensionAbility {
  onDestroy() {
    hilog.info(0x0000, TAG, `onDestroy`);
  }
}
```