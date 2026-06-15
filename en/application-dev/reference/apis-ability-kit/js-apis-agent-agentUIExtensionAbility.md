# @ohos.app.ability.AgentUIExtensionAbility (Agent Extension Ability with UI)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

AgentUIExtensionAbility inherits from [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md) and provides the Agent UI display capability on the access device.

[AgentExtensionAbility](./js-apis-app-agent-agentExtensionAbility.md) provides the Agent extension capability. AgentUIExtensionAbility must run in the same process as AgentExtensionAbility and cannot run independently.

For details about the inheritance relationship of each ability, see [Inheritance Relationship](./js-apis-app-ability-ability.md#ability-inheritance-relationship).

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs of this module cannot be used in [HAR](../../quick-start/har-package.md).

## Constraints

- The same initiator can start a maximum of five AgentUIExtensionAbility instances from the same provider at the same time.
- Windows and ArkUI components inside AgentUIExtensionAbility are not allowed to create sub-windows, nor can they be displayed in sub-windows.

## Modules to Import

```ts
import { AgentUIExtensionAbility } from '@kit.AbilityKit';
```

## AgentUIExtensionAbility

AgentUIExtensionAbility inherits from [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md) and provides the Agent UI display capability on the access device. For example, if an agent developer wants to display the result returned by the agent in another application, the agent developer can integrate AgentUIExtensionAbility to provide the capability of displaying an embedded pop-up window.

**System capability**: SystemCapability.Ability.AgentRuntime.Core
