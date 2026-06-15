# AgentExtensionContext (Agent Extension Ability Context)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

The AgentExtensionContext module is the context of the [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) and is inherited from [ExtensionContext](js-apis-inner-application-extensionContext.md).

AgentExtensionContext provides developers with the capability of accessing the [AgentCard](js-apis-inner-application-AgentCard.md) information configured for the current [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md) agent.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in the stage model.
> - In the example provided in this document, `this.context` is used to obtain `AgentExtensionContext`, where `this` indicates an instance inherited from `AgentExtensionAbility`.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## AgentExtensionContext

### Attribute

**Atomic service API**: This API can be used in atomic services since API version 24.

**System capability**: SystemCapability.Ability.AgentRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| agentCard | [AgentCard](js-apis-inner-application-AgentCard.md) | No| No| [AgentCard](js-apis-inner-application-AgentCard.md#agentcard-1) information configured for the current [AgentExtensionAbility](js-apis-app-agent-agentExtensionAbility.md).|

**Example:**

```ts
import { AgentExtensionAbility, common } from '@kit.AbilityKit';

export default class AgentExtension extends AgentExtensionAbility {
  onCreate(): void {
    let tmpContext: common.AgentExtensionContext = this.context; // Obtain AgentExtensionContext.
    console.info(`agentCard info data: ${JSON.stringify(tmpContext.agentCard)}.`);
  }
}
```
