# @ohos.bundle.overlay(overlay Module)

This module provides the capabilities of installing a featured application with the overlay feature, querying the [OverlayModuleInfo](arkts-ability-overlaymoduleinfo-i.md) information of the featured application, and disabling/enabling the featured application.

> **NOTE:** 
> 
> This page contains only the system APIs of this module. For other public APIs, see
> [@ohos.bundle.overlay](arkts-ability-bundle-overlay.md).

**Since:** 10

<!--Device-unnamed-declare namespace overlay--><!--Device-unnamed-declare namespace overlay-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Overlay

## Modules to Import

```TypeScript
import { overlay } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getoverlaymoduleinfo1) | Obtains the OverlayModuleInfo of the overlay feature module in the current application. This API uses an asynchronous callback to return the result. |
| [getOverlayModuleInfo](arkts-ability-overlay-getoverlaymoduleinfo-f.md#getoverlaymoduleinfo2) | Obtains the OverlayModuleInfo of the overlay feature module in the current application. This API uses a promise to return the result. If the API call fails, null may be returned. You need to verify the return value before using it. |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#gettargetoverlaymoduleinfos1) | Obtains the OverlayModuleInfo associated with the specified target module. Modules with the overlay feature generally provide an overlay resource file for other modules (target module) on the device. This API uses an asynchronous callback to return the result. |
| [getTargetOverlayModuleInfos](arkts-ability-overlay-gettargetoverlaymoduleinfos-f.md#gettargetoverlaymoduleinfos2) | Obtains the OverlayModuleInfo associated with the specified target module. Modules with the overlay feature generally provide an overlay resource file for other modules (target module) on the device. This API uses a promise to return the result. If the API call fails, null may be returned. You need to verify the return value before using it. |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setoverlayenabled1) | Sets the enabled/disabled state of the overlay feature module in the current application. This API uses an asynchronous callback to return the result. |
| [setOverlayEnabled](arkts-ability-overlay-setoverlayenabled-f.md#setoverlayenabled2) | Sets the enabled or disabled state of the overlay feature module in the current application. This API uses a promise to return the result. If the API call fails, null may be returned. You need to verify the return value before using it. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename1) | Obtains the information about all modules with the overlay feature in another application. This API uses an asynchronous callback to return the result. |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename2) | Obtains the information about a module with the overlay feature in another application. This API uses an asynchronous callback to return the result. |
| [getOverlayModuleInfoByBundleName](arkts-ability-overlay-getoverlaymoduleinfobybundlename-f-sys.md#getoverlaymoduleinfobybundlename3) | Obtains the OverlayModuleInfo information of the specified module in the specified application. This API uses a promise to return the result. |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename1) | Obtains the information about all modules with the overlay feature in another application. This API uses an asynchronous callback to return the result. |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename2) | Obtains the information about modules with the overlay feature in another application based on the target module name. This API uses an asynchronous callback to return the result. |
| [getTargetOverlayModuleInfosByBundleName](arkts-ability-overlay-gettargetoverlaymoduleinfosbybundlename-f-sys.md#gettargetoverlaymoduleinfosbybundlename3) | Obtains all OverlayModuleInfo information associated with the specified module in the specified application. This API uses a promise to return the result. |
| [setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setoverlayenabledbybundlename1) | Enables or disables a module with the overlay feature in another application. This API uses an asynchronous callback to return the result. |
| [setOverlayEnabledByBundleName](arkts-ability-overlay-setoverlayenabledbybundlename-f-sys.md#setoverlayenabledbybundlename2) | Enables or disables a module with the overlay feature in another application. This API uses a promise to return the result. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [OverlayModuleInfo](arkts-ability-overlay-overlaymoduleinfo-t.md) | OverlayModuleInfo contains the configuration information of the overlay feature module, such as its name, state, and target module, and is used to describe and manage the resource overlay configuration of an application. |
