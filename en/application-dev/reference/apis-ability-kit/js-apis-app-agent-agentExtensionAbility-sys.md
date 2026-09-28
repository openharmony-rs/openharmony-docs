# @ohos.app.agent.AgentExtensionAbility (Agent Extension Component) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7fe4eacae9c952d492316e40f501d71d3714186d translatedAt=2026-09-03T10:43:12.323Z pushedAt=2026-09-08T08:09:20.700Z -->

AgentExtensionAbility inherits from [ExtensionAbility](js-apis-app-ability-extensionAbility.md) and provides agent extension capabilities. This module provides the callback interface invoked when an Agent of the [LOW_CODE](js-apis-app-agent-agentConstant-sys.md#agentconstantagentcardtype) type is called, which is used to perform initialization operations (such as downloading resources from the cloud and loading configurations).

**Since**: 26.0.0

> **NOTE**
>
> This page contains only the system APIs of this module. For details about other public APIs, see [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md).
>
> The APIs of this module cannot be implemented or used in clone applications.

## Modules to Import

```ts
import { AgentExtensionAbility } from '@kit.AbilityKit';
```

## AgentExtensionAbility

### onAgentInvoked

onAgentInvoked(agentId: string): void

Triggered when an Agent of the [LOW_CODE](js-apis-app-agent-agentConstant-sys.md#agentconstantagentcardtype) type is successfully invoked, to perform initialization operations (such as downloading resources from the cloud and loading configurations).

**Since**: 26.0.0

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| agentId | string | Yes | ID of the Agent of the [LOW_CODE](js-apis-app-agent-agentConstant-sys.md#agentconstantagentcardtype) type. |

**Example**

```ts
import { AgentExtensionAbility } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[AgentExtensionAbility]';

export default class AgentExt extends AgentExtensionAbility {
  onAgentInvoked(agentId: string) {
    hilog.info(0x0000, TAG, `onAgentInvoked, agentId: ${agentId}`);
  }
}
```

