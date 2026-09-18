# requestRebuildHyperSnap

## Modules to Import

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## requestRebuildHyperSnap

```TypeScript
function requestRebuildHyperSnap(): void
```

Requests the recreation of the Hyper Snap process snapshot for the application.

When compatibility issues arise with an existing snapshot, this method triggers destruction of the current snapshot process. The system will subsequently generate a new snapshot at an optimal time to resolve compatibility problems while maintaining launch performance benefits.

**Notes:**  
- The system ultimately determines whether and when to recreate the snapshot. Invoking this method only submits  
a request; actual snapshot recreation depends on system policies and resource availability.  
- Recreation occurs during optimal system idle periods to minimize performance impact.  
- Primarily for resolving specific compatibility issues identified after initial snapshot creation.  
Most applications don't require manual intervention for snapshot management.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000150](../errorcode-ability.md#16000150-failed-to-send-request) | Failed to send request to system service. |
