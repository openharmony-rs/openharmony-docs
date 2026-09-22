# @ohos.bundle.overlay

The module provides APIs for querying the [OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md) of an application with the overlay feature, and disabling and enabling the feature.

An application with the overlay feature contains an overlay resource package. For details about this package, see [Overlay Mechanism](../../../quick-start/resource-categories-and-access.md#overlay-mechanism).

> **NOTE:** 
> 
> The APIs provided by this module apply only to the stage model and
> [static overlay](../../../quick-start/resource-categories-and-access.md#using-overlay-in-static-mode) mode.

**Since:** 10

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

## Modules to Import

```TypeScript
import { overlay } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getoverlaymoduleinfo) | Obtains the OverlayModuleInfo about a module with the overlay feature in the current application. This API uses an asynchronous callback to return the result. |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getoverlaymoduleinfo-1) | Obtains the OverlayModuleInfo about a module with the overlay feature in the current application. This API uses a promise to return the result. |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#gettargetoverlaymoduleinfos) | Obtains the OverlayModuleInfo associated with the specified target module. Modules with the overlay feature generally provide an overlay resource file for other modules (target module) on the device. This API uses an asynchronous callback to return the result. |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#gettargetoverlaymoduleinfos-1) | Obtains the OverlayModuleInfo associated with the specified target module. Modules with the overlay feature generally provide an overlay resource file for other modules (target module) on the device. This API uses a promise to return the result. |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setoverlayenabled) | Enables or disables a module with the overlay feature in the current application. This API uses an asynchronous callback to return the result. |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setoverlayenabled-1) | Enables or disables a module with the overlay feature in the current application. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename) | Obtains the information about all modules with the overlay feature in another application. This API uses an asynchronous callback to return the result. |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename-1) | Obtains the information about a module with the overlay feature in another application. This API uses an asynchronous callback to return the result. |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename-2) | Obtains the information about a module with the overlay feature in another application. This API uses a promise to return the result. |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename) | Obtains the information about all modules with the overlay feature in another application. This API uses an asynchronous callback to return the result. |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename-1) | Obtains the information about modules with the overlay feature in another application based on the target module name. This API uses an asynchronous callback to return the result. |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename-2) | Obtains the information about modules with the overlay feature in another application based on the target module name. This API uses a promise to return the result. |
| [setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setoverlayenabledbybundlename) | Enables or disables a module with the overlay feature in another application. This API uses an asynchronous callback to return the result. |
| [setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setoverlayenabledbybundlename-1) | Enables or disables a module with the overlay feature in another application. This API uses a promise to return the result. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md) | Defines the information about a module with the overlay feature. |
