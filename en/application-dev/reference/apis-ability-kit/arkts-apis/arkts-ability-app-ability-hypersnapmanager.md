# @ohos.app.ability.hyperSnapManager(Application Quick Startup Management)

The initialization process during app startup can be performed in advance as quick launch initialization, so that apps started via Quick Launch do not repeat the initialization process, thereby accelerating startup. The hyperSnapManager module provides Quick Launch management capabilities, including enabling or disabling the Quick Launch feature of an app and requesting re-initialization of Quick Launch.

> **NOTE:** 
> 
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a
> superscript to indicate their earliest API version.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace hyperSnapManager--><!--Device-unnamed-declare namespace hyperSnapManager-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Implementation Principle

Quick Launch initializes an app only once, which saves the time required for app initialization and AbilityStage creation during Quick Launch startup.

## Modules to Import

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getLastError](arkts-ability-hypersnapmanager-getlasterror-f.md#getlasterror-1) | Gets the last Hyper Snap error information of the current application for a specified scenario. Error information for each scenario is stored independently and cleared after a successful request. All error information will be cleared when the device restarts. |
| [isHyperSnapInitializing](arkts-ability-hypersnapmanager-ishypersnapinitializing-f.md#ishypersnapinitializing-1) | Checks whether the current process is undergoing Hyper Snap initialization. This API uses a promise to return the result. |
| [requestRebuildHyperSnap](arkts-ability-hypersnapmanager-requestrebuildhypersnap-f.md#requestrebuildhypersnap-1) | Requests the recreation of the Hyper Snap process snapshot for the application. |
| [setHyperSnapEnabled](arkts-ability-hypersnapmanager-sethypersnapenabled-f.md#sethypersnapenabled-1) | Enables or disables the Hyper Snap performance optimization for the application. |

### Interfaces

| Name | Description |
| --- | --- |
| [HyperSnapErrorInfo](arkts-ability-hypersnapmanager-hypersnaperrorinfo-i.md) | Describes the Hyper Snap error information. |

### Enums

| Name | Description |
| --- | --- |
| [HyperSnapErrorCode](arkts-ability-hypersnapmanager-hypersnaperrorcode-e.md) | Enumerates the Hyper Snap error codes. |
| [HyperSnapErrorType](arkts-ability-hypersnapmanager-hypersnaperrortype-e.md) | Enumerates the Hyper Snap error type. |
