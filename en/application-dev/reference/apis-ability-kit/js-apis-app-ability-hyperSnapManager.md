# @ohos.app.ability.hyperSnapManager (Application Snapshot Management)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The initialization process during application startup can be created as an application snapshot in advance. Applications started from the snapshot do not need to repeat the initialization process, thereby accelerating the startup. The hyperSnapManager module provides the capability of managing application snapshots, including enabling or disabling the snapshot function of an application and requesting the re-creation of an application snapshot.

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Principle

An application snapshot is created only once. Starting from the application snapshot saves the time required for application initialization and AbilityStage creation.

**Figure 1** Snapshot startup process

![Snapshot-Start](./figures/Snapshot-Start.png)

## Modules to Import

```ts
import { hyperSnapManager } from '@kit.AbilityKit';
```

## hyperSnapManager.setHyperSnapEnabled

setHyperSnapEnabled(enableFlag: boolean): void

Enables or disables the snapshot function for an application.

> **NOTE**
>
> - When the application snapshot function is enabled through this API, the system determines whether to create or use a snapshot based on the application compatibility, resource availability, and system policy. When the snapshot function is disabled through this API, the system will not create snapshots.
> - The configured value will be retained after a restart.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters:**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| enableFlag | boolean | Yes| Indicates the switch flag of the snapshot function.<br>- `true`: indicates that the snapshot function is enabled. (The system determines whether to create a snapshot.)<br>- `false`: indicates that the snapshot function is disabled.|

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error Code| Error Message|
| ------- | -------- |
| 16000150 | Failed to send request to system service. |

**Example:**

```ts
import { hyperSnapManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Enable the application snapshot function.
  hyperSnapManager.setHyperSnapEnabled(true);
  console.info('Hyper Snap enabled successfully.');
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to enable Hyper Snap. Code: ${code}, Message: ${message}`);
}
```

## hyperSnapManager.requestRebuildHyperSnap

requestRebuildHyperSnap(): void

Requests to recreate the application snapshot.

This method destroys the snapshot corresponding to the current process. The system will generate a new snapshot at a proper time.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| Error Code| Error Message|
| ------- | -------- |
| 16000150 | Failed to send request to system service. |

**Example:**

```ts
import { hyperSnapManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Request to recreate the application snapshot.
  hyperSnapManager.requestRebuildHyperSnap();
  console.info('Requested to rebuild Hyper Snap successfully.');
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to request Hyper Snap rebuild. Code: ${code}, Message: ${message}`);
}
```
