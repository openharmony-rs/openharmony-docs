# @ohos.app.ability.abilityManager

The AbilityManager module provides APIs for obtaining, adding, and updating ability information and running status information.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAbilityRunningInfos](arkts-ability-abilitymanager-getabilityrunninginfos-f.md) | Obtains the UIAbility running information. This API uses a promise to return the result. |
| [isEmbeddedUIExtensionSupported](arkts-ability-abilitymanager-isembeddeduiextensionsupported-f.md) | Indicates whether the current device supports EmbeddedUIExtensionAbility. |
| [restartSelfAtomicService](arkts-ability-abilitymanager-restartselfatomicservice-f.md) | Restarts the current atomic service. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [acquireShareData](arkts-ability-abilitymanager-acquiresharedata-f-sys.md) | Called by a system dialog box to obtain shared data, which is set by the target UIAbility through [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare). This API uses an asynchronous callback to return the result. |
| [acquireShareData](arkts-ability-abilitymanager-acquiresharedata-f-sys.md#acquiresharedata-2) | Called by a system dialog box to obtain shared data, which is set by the target UIAbility through [onShare](arkts-ability-app-ability-uiability-uiability-c.md#onshare). This API uses a promise to return the result. |
| [clearPreloadedUIExtensionAbilities](arkts-ability-abilitymanager-clearpreloadeduiextensionabilities-f-sys.md) | Clears all preloaded [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instances in the current process. This API uses a promise to return the result. |
| [clearPreloadedUIExtensionAbility](arkts-ability-abilitymanager-clearpreloadeduiextensionability-f-sys.md) | Clears a [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instance. This API uses a promise to return the result. |
| [getAbilityRunningInfos](arkts-ability-abilitymanager-getabilityrunninginfos-f-sys.md#getabilityrunninginfos-1) | Obtains the UIAbility running information. This API uses an asynchronous callback to return the result. |
| [getExtensionRunningInfos](arkts-ability-abilitymanager-getextensionrunninginfos-f-sys.md#getextensionrunninginfos) | Obtains the ExtensionAbility running information. This API uses a promise to return the result. |
| [getExtensionRunningInfos](arkts-ability-abilitymanager-getextensionrunninginfos-f-sys.md#getextensionrunninginfos-1) | Obtains the ExtensionAbility running information. This API uses an asynchronous callback to return the result. |
| [getForegroundUIAbilities](arkts-ability-abilitymanager-getforegrounduiabilities-f-sys.md#getforegrounduiabilities) | Obtains the information about the UIAbility components of an application that is running in the foreground. This API uses an asynchronous callback to return the result. |
| [getForegroundUIAbilities](arkts-ability-abilitymanager-getforegrounduiabilities-f-sys.md#getforegrounduiabilities-1) | Obtains the information about the UIAbility components of an application that is running in the foreground. This API uses a promise to return the result. |
| [getTopAbility](arkts-ability-abilitymanager-gettopability-f-sys.md#gettopability) | Obtains the top ability, which is the ability that has the window focus. This API uses a promise to return the result. |
| [getTopAbility](arkts-ability-abilitymanager-gettopability-f-sys.md#gettopability-1) | Obtains the top ability, which is the ability that has the window focus. This API uses an asynchronous callback to return the result. |
| [isEmbeddedOpenAllowed](arkts-ability-abilitymanager-isembeddedopenallowed-f-sys.md) | Checks whether the [EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md) can be started in embedded mode. This API uses a promise to return the result. |
| [notifyDebugAssertResult](arkts-ability-abilitymanager-notifydebugassertresult-f-sys.md) | Notifies the application of the assertion result. This API uses a promise to return the result. |
| [notifySaveAsResult](arkts-ability-abilitymanager-notifysaveasresult-f-sys.md#notifysaveasresult) | Used by the [Data Loss Prevention (DLP)](../../apis-data-protection-kit/arkts-apis/arkts-dataprotection-dlppermission.md) management application to notify a sandbox application of the data saving result. This API uses an asynchronous callback to return the result. |
| [notifySaveAsResult](arkts-ability-abilitymanager-notifysaveasresult-f-sys.md#notifysaveasresult-1) | Used by the [Data Loss Prevention (DLP)](../../apis-data-protection-kit/arkts-apis/arkts-dataprotection-dlppermission.md) management application to notify a sandbox application of the data saving result. This API uses a promise to return the result. |
| [off](arkts-ability-abilitymanager-off-f-sys.md#offabilityforegroundstate) | Unregisters the observer used to listen for ability start or exit events. |
| [offPreloadedUIExtensionAbilityDestroyed](arkts-ability-abilitymanager-offpreloadeduiextensionabilitydestroyed-f-sys.md) | Unsubscribes from loaded events of a preloaded [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instance in the current process. |
| [offPreloadedUIExtensionAbilityLoaded](arkts-ability-abilitymanager-offpreloadeduiextensionabilityloaded-f-sys.md) | Unsubscribes from loaded events of a preloaded [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instance in the current process. |
| [on](arkts-ability-abilitymanager-on-f-sys.md#onabilityforegroundstate) | Registers an observer to listen for ability start or exit events. |
| [onPreloadedUIExtensionAbilityDestroyed](arkts-ability-abilitymanager-onpreloadeduiextensionabilitydestroyed-f-sys.md) | Subscribes to destroyed events of a preloaded [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instance in the current process. |
| [onPreloadedUIExtensionAbilityLoaded](arkts-ability-abilitymanager-onpreloadeduiextensionabilityloaded-f-sys.md) | Subscribes to loaded events of a preloaded [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instance in the current process. |
| [preloadUIExtensionAbility](arkts-ability-abilitymanager-preloaduiextensionability-f-sys.md) | Preloads a [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instance and returns the instance ID. This API uses a promise to return the result. Use this API when the application needs to preload a UIExtensionAbility to improve startup performance. |
| [queryAtomicServiceStartupRule](arkts-ability-abilitymanager-queryatomicservicestartuprule-f-sys.md) | Obtains the rule for launching an [EmbeddableUIAbility](arkts-ability-app-ability-embeddableuiability-embeddableuiability-c.md) in embedded mode. This API uses a promise to return the result. This API can be properly called only on phones and tablets. On other devices, it returns the error code 801. |
| [setResidentProcessEnabled](arkts-ability-abilitymanager-setresidentprocessenabled-f-sys.md) | Enables or disables the resident process of an application. |
| [updateConfiguration](arkts-ability-abilitymanager-updateconfiguration-f-sys.md#updateconfiguration) | Updates the configuration. This API uses an asynchronous callback to return the result. |
| [updateConfiguration](arkts-ability-abilitymanager-updateconfiguration-f-sys.md#updateconfiguration-1) | Updates the configuration. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AtomicServiceStartupRule](arkts-ability-abilitymanager-atomicservicestartuprule-i-sys.md) | Describes the rule for launching an embedded atomic service. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AbilityState](arkts-ability-abilitymanager-abilitystate-e.md) | Enumerates the ability states. This enum can be used together with [AbilityRunningInfo](arkts-ability-abilityrunninginfo-i.md) to return the ability state. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [UserStatus](arkts-ability-abilitymanager-userstatus-e-sys.md) | Enumerates the assertion result for different user operations. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [AbilityRunningInfo](arkts-ability-abilitymanager-abilityrunninginfo-t.md) | Defines the level-2 module AbilityRunningInfo. |
| [AbilityStateData](arkts-ability-abilitymanager-abilitystatedata-t.md) | Defines the level-2 module AbilityStateData. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [AbilityForegroundStateObserver](arkts-ability-abilitymanager-abilityforegroundstateobserver-t-sys.md) | Defines the level-2 module AbilityForegroundStateObserver. |
| [ExtensionRunningInfo](arkts-ability-abilitymanager-extensionrunninginfo-t-sys.md) | Defines the level-2 module ExtensionRunningInfo. |
| [PreloadedUIExtensionAbilityDestroyedFn](arkts-ability-abilitymanager-preloadeduiextensionabilitydestroyedfn-t-sys.md) | Defines the callback function when the preloaded [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instance is destroyed. |
| [PreloadedUIExtensionAbilityLoadedFn](arkts-ability-abilitymanager-preloadeduiextensionabilityloadedfn-t-sys.md) | Defines the callback function when the preloaded [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) instance is loaded. |
<!--DelEnd-->
