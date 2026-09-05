# AbilityStateData

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=27b6f4111ead7a083f316fdee6f7ca15eaa4c87b translatedAt=2026-09-03T11:38:29.376Z pushedAt=2026-09-05T10:47:30.663Z -->

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
| uid                    | number   | No   | No   | UID of the application.                  |
| state                   | number   | No   | No   | Ability state.<br>- [Stage model](../../application-models/ability-terminology.md#stage-model): For the state of [UIAbility](js-apis-app-ability-uiAbility.md), see [UIAbility State](#uiability-state); for the state of [ExtensionAbility](js-apis-app-ability-extensionAbility.md), see [ExtensionAbility State](#extensionability-state); for the state of [UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md), see [UIExtensionAbility State](#uiextensionability-state).<br>- [FA model](../../application-models/ability-terminology.md#fa-model): See [Ability State](#ability-state-fa-model).                |
| moduleName | string   | No  | No  | Module name to which the ability belongs.   |
| abilityType | number | No  | No  | [Ability type](#ability-types), which can be [UIAbility](js-apis-app-ability-uiAbility.md) or [ExtensionAbility](js-apis-app-ability-extensionAbility.md).|
| isAtomicService | boolean | No| No| Whether the ability belongs to an atomic service.<br>**true**: The ability belongs to an atomic service.<br>**false**: The ability does not belong to an atomic service.|
| appCloneIndex          | number   | No   | Yes   | Index of the [app clone](../../quick-start/app-clone.md) of the application package. The value **0** indicates the main instance, and a value greater than or equal to **1** indicates a clone instance. If this parameter is not returned, the main instance is used by default. |
| callerBundleName<sup>23+</sup> | string | No| Yes| Bundle name of the application that triggers the creation of the ability.|

### UIAbility States

| Value | Description |
| ----- | ---------------------- |
| 0 | The UIAbility is being created. |
| 1 | The UIAbility has been created. |
| 2 | The UIAbility is in the foreground. |
| 3 | The UIAbility has gained focus. |
| 4 | The UIAbility is in the background. |
| 5 | The UIAbility has been destroyed. |

### ExtensionAbility States
| Value | Description |
| ----- | ---------------------- |
| 0 | The ExtensionAbility is being created. |
| 1 | The ExtensionAbility has been created. |
| 2 | The ExtensionAbility has established a connection with the client. |
| 3 | The ExtensionAbility is disconnected from the client. |
| 4 | The ExtensionAbility is normally destroyed because all clients are disconnected. |
| 5 | The ExtensionAbility has been destroyed. This covers normal destruction (including that triggered by disconnection of all clients) and abnormal destruction (for example, the process where it resides is killed). |

### UIExtensionAbility States

| Value | Description |
| ----- | ---------------------- |
| 0 | The UIExtensionAbility is being created. |
| 1 | The UIExtensionAbility has been created. |
| 2 | The UIExtensionAbility is in the foreground. |
| 4 | The UIExtensionAbility is in the background. |
| 5 | The UIExtensionAbility has been destroyed. |

### Ability States (FA Model)

| Value | Description |
| ---- | ---------------------- |
| 0    | The ability is being created. |
| 1    | The ability has been created. |
| 2    | The ability is in the foreground. |
| 3    | The ability has gained focus. |
| 4    | The ability is in the background. |
| 5    | The ability has been destroyed. |
| 7    | The background service is connected by the client. |
| 8    | The background service is disconnected from the client. |

### Ability Types

| Value | Description |
| ---- | --------------------- |
| 0    | Unknown type. (System error) |
| 1    | Ability of the UI type, that is, [UIAbility](js-apis-app-ability-uiAbility.md). |
| 2    | Ability of the background service type. (FA model) |
| 3    | Ability of the data type. (FA model) |
| 4    | Ability of the widget type. (FA model) |
| 5    | Ability of the extension type. (Stage model) |
