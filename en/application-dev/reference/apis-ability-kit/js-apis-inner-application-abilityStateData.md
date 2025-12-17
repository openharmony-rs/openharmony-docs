# AbilityStateData

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->
The AbilityStateData module defines a struct for ability state information. Once a lifecycle change listener is registered using [on](js-apis-app-ability-appManager.md#appmanageronapplicationstate14), you can obtain an instance of this struct from the input parameter of the **onAbilityStateChanged** callback of [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md).

> **NOTE**
> 
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## AbilityStateData


**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                    | Type    | Read-Only| Optional| Description                      |
| ----------------------- | ---------| ---- | ---- | ------------------------- |
| pid                     | number   | No  | No  | Process ID.                   |
| bundleName              | string   | No  | No | Bundle name.         |
| abilityName            | string   | No  | No  | Ability name.              |
| uid                    | number   | No  | No  | UID of the application.                 |
| state                   | number   | No  | No  | Ability state.<br>- [Stage model](../../application-models/ability-terminology.md#stage-model): For the [UIAbility](js-apis-app-ability-uiAbility.md), see [UIAbility States](#uiability-states). For the [ExtensionAbility](js-apis-app-ability-extensionAbility.md), see [ExtensionAbility States](#extensionability-states). For the [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md), see [UIExtensionAbility States](#uiextensionability-states).<br>- [FA model](../../application-models/ability-terminology.md#fa-model): For the ability, see [Ability States](#ability-states).               |
| moduleName | string   | No  | No  | Module name to which the ability belongs.   |
| abilityType | number | No  | No  | [Ability type](#ability-types), which can be [UIAbility](js-apis-app-ability-uiAbility.md) or [ExtensionAbility](js-apis-app-ability-extensionAbility.md).|
| isAtomicService | boolean | No| No| Whether the ability belongs to an atomic service.<br>**true**: The ability belongs to an atomic service.<br>**false**: The ability does not belong to an atomic service.|
| appCloneIndex          | number   | No  | Yes  | Index of an [application clone](../../quick-start/app-clone.md).                 |
| callerBundleName<sup>23+</sup> | string | No| Yes| Bundle name of the application that triggers the creation of the ability.|

### UIAbility States

| Value  | State                      | Description                  |
| ---- | -------------------------- | ---------------------- |
| 0    | ABILITY_STATE_CREATE       | The UIAbility is being created.     |
| 1    | ABILITY_STATE_READY        | The UIAbility has been created.     |
| 2    | ABILITY_STATE_FOREGROUND   | The UIAbility is running in the foreground.       |
| 3    | ABILITY_STATE_FOCUS        | The UIAbility has gained focus.       |
| 4    | ABILITY_STATE_BACKGROUND   | The UIAbility is running in the background.       |
| 5    | ABILITY_STATE_TERMINATED   | The UIAbility is terminated.       |

### ExtensionAbility States
| Value  | State   | Description                 |
| ---- | -------------------------- | ---------------------- |
| 0    | EXTENSION_STATE_CREATE     | The ExtensionAbility is being created. |
| 1    | EXTENSION_STATE_READY      | The ExtensionAbility has been created. |
| 2    | EXTENSION_STATE_CONNECTED  | The ExtensionAbility is connected to the client.|
| 3    | EXTENSION_STATE_DISCONNECTED | The ExtensionAbility is disconnected from the client.|
| 4    | EXTENSION_STATE_TERMINATED  | The ExtensionAbility is terminated. |

### UIExtensionAbility States

| Value  | State                      | Description                  |
| ---- | -------------------------- | ---------------------- |
| 0    | ABILITY_STATE_CREATE       | The UIExtensionAbility is being created.     |
| 1    | ABILITY_STATE_READY        | The UIExtensionAbility has been created.     |
| 2    | ABILITY_STATE_FOREGROUND   | The UIExtensionAbility is running in the foreground.       |
| 4    | ABILITY_STATE_BACKGROUND   | The UIExtensionAbility is running in the background.       |
| 5    | ABILITY_STATE_TERMINATED   | The UIExtensionAbility is terminated.       |

### Ability States

| Value  | State                      | Description                  |
| ---- | -------------------------- | ---------------------- |
| 0    | ABILITY_STATE_CREATE       | The ability is being created.     |
| 1    | ABILITY_STATE_READY        | The ability has been created.     |
| 2    | ABILITY_STATE_FOREGROUND   | The ability is running in the foreground.       |
| 3    | ABILITY_STATE_FOCUS        | The ability has gained focus.      |
| 4    | ABILITY_STATE_BACKGROUND   | The ability is running in the background.       |
| 5    | ABILITY_STATE_TERMINATED   | The ability is terminated.       |
| 7    | ABILITY_STATE_CONNECTED    | The background service is connected to the client.|
| 8    | ABILITY_STATE_DISCONNECTED | The background service is disconnected from the client.|

### Ability Types

| Value  | State   | Description                 |
| ---- | ------- | --------------------- |
| 0    | UNKNOWN | Unknown type. (System error.)             |
| 1    | PAGE    | Ability that provides the UI, that is, [UIAbility](js-apis-app-ability-uiAbility.md). |
| 2    | SERVICE | Ability that provides the background service. (FA model.)|
| 3    | DATA | Ability that provides the data service. (FA model.)              |
| 4    | FORM    | Ability that provides the widget service. (FA model.)   |
| 5    | EXTENSION | Ability that provides the extension service. (stage model.) |
