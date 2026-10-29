# isHyperSnapInitializing

## Modules to Import

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## isHyperSnapInitializing

```TypeScript
function isHyperSnapInitializing(): Promise<boolean>
```

Checks whether the current process is undergoing Hyper Snap initialization. This API uses a promise to return the result.

During the Hyper Snap template process initialization (including preloading and image creation phases), this method returns **true**. Once the snapshot is complete, fails, or the process is not a template process, this method returns **false**.

This is useful for applications to distinguish between a normal cold start and a Hyper Snap template process initialization, allowing them to adjust their initialization logic accordingly.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-hyperSnapManager-function isHyperSnapInitializing(): Promise<boolean>--><!--Device-hyperSnapManager-function isHyperSnapInitializing(): Promise<boolean>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates the current process is undergoing Hyper Snap initialization, and **false** indicates the current process is not undergoing Hyper Snap initialization (snapshot completed, failed, or the process is not a template process). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Connect to system service failed. |
