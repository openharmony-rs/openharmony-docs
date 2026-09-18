# @ohos.app.ability.application(Application Utility Class)

You can use this module to create a [Context](../../../application-models/application-context-stage.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { application } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createModuleContext](arkts-ability-application-createmodulecontext-f.md) | Creates the context for a module. The [resourceManager.Configuration](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-configuration-c.md) in the created module context inherits from the input context, making it convenient for you to access [application resources across HAP/HSP packages](../../../quick-start/resource-categories-and-access.md#cross-haphsp-resources). This API uses a promise to return the result. |
| [createModuleContextSync](arkts-ability-application-createmodulecontextsync-f.md) | Creates the context for a module. The [resourceManager.Configuration](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-configuration-c.md) in the created module context inherits from the input context, making it convenient for you to access [application resources across HAP/HSP packages](../../../quick-start/resource-categories-and-access.md#cross-haphsp-resources) |
| [createPluginModuleContext](arkts-ability-application-createpluginmodulecontext-f.md) | Creates the context of a plugin under the current application based on the context, plugin bundle name, and plugin module name, so as to obtain the basic information about the plugin. This API uses a promise to return the result. |
| [demoteCurrentFromCandidateMasterProcess](arkts-ability-application-demotecurrentfromcandidatemasterprocess-f.md) | Removes the current process from the candidate master process list. This API uses a promise to return the result. This API can be properly called on PCs/2-in-1 devices and tablets. If it is called on other devices, error code 801 is returned. **System capability**: SystemCapability.Ability.AbilityRuntime.Core |
| [exitMasterProcessRole](arkts-ability-application-exitmasterprocessrole-f.md) | Relinquishes the [master-process](../../../application-models/ability-terminology.md#master-process) role from the current process. This API uses a promise to return the result. This API can be properly called only on 2-in-1 devices and tablets. If it is called on other device types, error code 801 is returned. |
| [getApplicationContext](arkts-ability-application-getapplicationcontext-f.md) | Obtains the application context. This API provides context access independent of the base class **Context**. Repeated calls to this API generate a new ApplicationContext object. |
| [getApplicationContextInstance](arkts-ability-application-getapplicationcontextinstance-f.md) | Obtains the application context. This API provides context access independent of the base class **Context**. Repeated calls to this API obtain the same ApplicationContext instance. |
| [getAppPreloadType](arkts-ability-application-getapppreloadtype-f.md) | Obtains the preloading type of the current application process. |
| [promoteCurrentToCandidateMasterProcess](arkts-ability-application-promotecurrenttocandidatemasterprocess-f.md) | Adds the current process into the [candidate master process](../../../application-models/ability-terminology.md#candidate-master-process) list. This API uses a promise to return the result. When the [master process](../../../application-models/ability-terminology.md#master-process) is destroyed and a UIAbility or UIExtensionAbility with **isolationProcess** set to **true** is restarted, the system takes corresponding actions based on whether there is a candidate master process. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createBundleContext](arkts-ability-application-createbundlecontext-f-sys.md) | Creates the context for an application. This API uses a promise to return the result. |
| [createModuleContext](arkts-ability-application-createmodulecontext-f-sys.md) | Creates the context for a module. This API uses a promise to return the result. |
| [createPluginModuleContextForHostBundle](arkts-ability-application-createpluginmodulecontextforhostbundle-f-sys.md) | Creates the context for a plugin based on a given context, plugin bundle name, plugin module name, and application bundle name to obtain the basic information about the plugin. This API uses a promise to return the result. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AppPreloadType](arkts-ability-application-apppreloadtype-e.md) | Enumerates the preloading types of the current application process. |
