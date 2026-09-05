# @ohos.app.ability.insightIntent (Basic Definitions of InsightIntent Framework) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=56120e9987a6cf60223e410520046a2af38081c3 translatedAt=2026-09-03T10:18:24.148Z pushedAt=2026-09-05T10:47:30.392Z -->

This module provides basic definitions of the [InsightIntent framework](../../application-models/insight-intent-overview.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.app.ability.insightIntent (Basic Definitions of InsightIntent Framework)](js-apis-app-ability-insightIntent.md).

## Modules to Import

```ts
import { insightIntent } from '@kit.AbilityKit';
```

## ExecuteMode

Intent execution mode. Indicates the mode passed when a system entry triggers intent execution. The execution modes supported by each intent are defined during intent development.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Value| Description|
| -------- | -------- | -------- |
| SERVICE_EXTENSION_ABILITY | 3 | Starts a ServiceExtensionAbility.<br>**System API:** This API is a system API. |

## ExecuteResult

Return result of intent execution.

**Since**: 26.1.0

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| interactionInfo | [InteractionInfo](#interactioninfo) | No | Yes | Interactive information returned after intent execution. |

## InteractionUI

Defines the information about the interactive interface to be displayed after the current intent execution is complete.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Readable | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| interactionUIType | string | No | No | Type of the interactive interface. |

## InteractionModalUIExtension

Defines the information to be displayed as an interactive interface by a modal UIExtension when intent execution is complete. Distributed scenarios are not supported. Inherits from [InteractionUI](#interactionui).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| interactionUIType | string | No | No | Type of the interactive interface, fixed to 'MODAL_UIEXTENSION'. |
| bundleName | string | No | No | Bundle name of the target UIExtension ability. |
| moduleName | string | No | No | Module name of the target UIExtension ability. |
| abilityName | string | No | No | Ability name of the target UIExtension ability. |
| uiExtensionType | string | No | No | Type of the UIExtension. |
| uri | string | No | No | URI information passed to the target UIExtension. |
| parameters | Record\<string, Object\> | No | No | Parameters passed to the target UIExtension. |

## InteractionInfo

Defines the interactive information returned after the current intent execution is complete.

**Since**: 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| interactionUI | [InteractionUI](#interactionui) | No | Yes | Interactive interface information to be displayed after the current intent execution is complete. |

