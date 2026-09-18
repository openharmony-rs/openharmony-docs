# @ohos.app.ability.hyperSnapManager(Application Quick Startup Management)

This module provides the capability to manage HyperSnap.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getLastError](arkts-ability-hypersnapmanager-getlasterror-f.md) | Gets the last Hyper Snap error information of the current application for a specified scenario. Error information for each scenario is stored independently and cleared after a successful request. All error information will be cleared when the device restarts. |
| [requestRebuildHyperSnap](arkts-ability-hypersnapmanager-requestrebuildhypersnap-f.md) | Requests the recreation of the Hyper Snap process snapshot for the application. |
| [setHyperSnapEnabled](arkts-ability-hypersnapmanager-sethypersnapenabled-f.md) | Enables or disables the Hyper Snap performance optimization for the application. |

### Interfaces

| Name | Description |
| --- | --- |
| [HyperSnapErrorInfo](arkts-ability-hypersnapmanager-hypersnaperrorinfo-i.md) | Describes the Hyper Snap error information. |

### Enums

| Name | Description |
| --- | --- |
| [HyperSnapErrorCode](arkts-ability-hypersnapmanager-hypersnaperrorcode-e.md) | Enumerates the Hyper Snap error codes. |
| [HyperSnapErrorType](arkts-ability-hypersnapmanager-hypersnaperrortype-e.md) | Enumerates the Hyper Snap error type. |
