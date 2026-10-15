# @ohos.ability.featureAbility(FeatureAbility Module)

The FeatureAbility module provides APIs that enable user interaction. You can use the APIs to start or terminate an ability, obtain a dataAbilityHelper object, obtain the window corresponding to the current ability, and connect to or disconnect from a ServiceAbility.

**Since:** 6

<!--Device-unnamed-declare namespace featureAbility--><!--Device-unnamed-declare namespace featureAbility-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

## Modules to Import

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [acquireDataAbilityHelper](arkts-ability-featureability-acquiredataabilityhelper-f.md#acquiredataabilityhelper) | Obtains a dataAbilityHelper object. |
| [connectAbility](arkts-ability-featureability-connectability-f.md#connectability) | Connects this ability to a ServiceAbility. |
| [disconnectAbility](arkts-ability-featureability-disconnectability-f.md#disconnectability1) | Disconnects this ability from a specific ServiceAbility. This API uses an asynchronous callback to return the result. |
| [disconnectAbility](arkts-ability-featureability-disconnectability-f.md#disconnectability2) | Disconnects this ability from a specific ServiceAbility. This API uses a promise to return the result. |
| [getContext](arkts-ability-featureability-getcontext-f.md#getcontext) | Obtains the application context. |
| [getWant](arkts-ability-featureability-getwant-f.md#getwant1) | Obtains the Want corresponding to the ability to start. This API uses an asynchronous callback to return the result. |
| [getWant](arkts-ability-featureability-getwant-f.md#getwant2) | Obtains the Want corresponding to the ability to start. This API uses a promise to return the result. |
| [getWindow](arkts-ability-featureability-getwindow-f.md#getwindow1) | Obtains the window corresponding to this ability. This API uses an asynchronous callback to return the result. |
| [getWindow](arkts-ability-featureability-getwindow-f.md#getwindow2) | Obtains the window corresponding to this ability. This API uses a promise to return the result. |
| [hasWindowFocus](arkts-ability-featureability-haswindowfocus-f.md#haswindowfocus1) | Checks whether the main window of this ability has the focus. This API uses an asynchronous callback to return the result. |
| [hasWindowFocus](arkts-ability-featureability-haswindowfocus-f.md#haswindowfocus2) | Checks whether the main window of this ability has the focus. This API uses a promise to return the result. |
| [startAbility](arkts-ability-featureability-startability-f.md#startability1) | Starts an ability. This API uses an asynchronous callback to return the result. |
| [startAbility](arkts-ability-featureability-startability-f.md#startability2) | Starts an ability. This API uses a promise to return the result. |
| [startAbilityForResult](arkts-ability-featureability-startabilityforresult-f.md#startabilityforresult1) | Starts an ability. This API uses an asynchronous callback to return the result. The following situations may be possible for a started ability: |
| [startAbilityForResult](arkts-ability-featureability-startabilityforresult-f.md#startabilityforresult2) | Starts an ability. This API uses a promise to return the result. The following situations may be possible for a started ability: |
| [terminateSelf](arkts-ability-featureability-terminateself-f.md#terminateself1) | Terminates this ability. This API uses an asynchronous callback to return the result. |
| [terminateSelf](arkts-ability-featureability-terminateself-f.md#terminateself2) | Terminates this ability. This API uses a promise to return the result. |
| [terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult1) | Terminates this ability. This API uses an asynchronous callback to return the result. If the ability is started by calling [startAbilityForResult](arkts-ability-featureability-startabilityforresult-f.md#startabilityforresult1), the result is returned to the caller when **terminateSelfWithResult** is called. Otherwise, no result is returned to the caller when **terminateSelfWithResult** is called. |
| [terminateSelfWithResult](arkts-ability-featureability-terminateselfwithresult-f.md#terminateselfwithresult2) | Terminates this ability. This API uses a promise to return the result. If the ability is started by calling [startAbilityForResult](arkts-ability-featureability-startabilityforresult-f.md#startabilityforresult1), the result is returned to the caller when **terminateSelfWithResult** is called. Otherwise, no result is returned to the caller when **terminateSelfWithResult** is called. |

### Types

| Name | Description |
| --- | --- |
| [AppVersionInfo](arkts-ability-featureability-appversioninfo-t.md) | Defines an AppVersionInfo object. |
| [Context](arkts-ability-featureability-context-t.md) | Defines the Context module. |
| [ProcessInfo](arkts-ability-featureability-processinfo-t.md) | Defines a ProcessInfo object. |

### Enums

| Name | Description |
| --- | --- |
| [AbilityStartSetting](arkts-ability-featureability-abilitystartsetting-e.md) | Defines the window property corresponding to this ability. The **abilityStartSetting** property is an object defined in the format of [**key: string]: any**, where **key** is an enumerated value of ** AbilityStartSetting** and **value** is an enumerated value of **AbilityWindowConfiguration**. |
| [AbilityWindowConfiguration](arkts-ability-featureability-abilitywindowconfiguration-e.md) | Defines the window configuration corresponding to this ability. The configuration is obtained through **featureAbility.AbilityWindowConfiguration**. |
| [DataAbilityOperationType](arkts-ability-featureability-dataabilityoperationtype-e.md) | Enumerates the operation types of a DataAbility. The DataAbility can use an enumerated value to specify the operation type when operating data in batches. |
| [ErrorCode](arkts-ability-featureability-errorcode-e.md) | Enumerates the error codes that may be returned when an ability is started. |
