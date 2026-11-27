# @ohos.app.ability.hyperSnapManager (Application Quick Startup Management)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=425050ef4ca288a92ed7cdeb46e5ed6815668b91 translatedAt=2026-11-25T11:23:48.103Z pushedAt=2026-11-26T02:33:59.950Z nl=1 -->

The initialization process during application startup can be performed in advance as fast startup initialization, so that applications launched via fast startup do not repeat the initialization process, thereby accelerating startup. The hyperSnapManager module provides app fast startup management capabilities, including enabling or disabling the app's fast startup function, requesting to reinitialize app fast startup, and querying fast startup error information.

> **NOTE**
>
> The initial APIs of this module are supported since API version 24. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Working Principles

Quick Launch initializes an app only once, which saves the time required for app initialization and AbilityStage creation during Quick Launch startup.

**Figure 1** Quick Launch startup process


## Modules to Import

```ts
import { hyperSnapManager } from '@kit.AbilityKit';
```

## HyperSnapErrorType

Represents the scenarios in which fast startup errors occur. Users can pass different error scenario enum values to obtain error information for different fast startup scenarios.

**Since:** 26.0.1

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model Constraint:** This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| CREATE_SNAPSHOT | 0 | Various scenarios caused by snapshot creation failure during fast startup initialization. |
| FORK_FROM_SNAPSHOT | 1 | Various scenarios caused by failure to create a new process from the snapshot during fast startup. |

## HyperSnapErrorCode

Represents the error codes of fast startup errors.

**Since:** 26.0.1

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model Constraint:** This API can be used only in the stage model.

| Name | Value | Description |
| -------- | -------- | -------- |
| ERR_OK | 0 | No fast startup error occurs, or fast startup is not triggered. |
| ERR_SYSTEM_INNER | 1 | Internal system error. |
| ERR_SNAPSHOT_EXIST | 2 | A snapshot has been successfully created during fast startup initialization, and triggering the fast startup initialization process again is illegal. |
| ERR_PROCESS_IS_RUNNING | 3 | The application process is running when the system prepares to perform app fast startup initialization. |
| ERR_SNAPSHOT_PROCESS_IS_DIED | 4 | The process used to create the snapshot is terminated during snapshot creation in fast startup initialization. |
| ERR_SNAPSHOT_IS_INTERRUPTED | 5 | The user launches the application when the system prepares to perform app fast startup initialization. |
| ERR_EXISTS_ILLEGAL_BINDER | 6 | The application has an illegal Binder. |
| ERR_LAST_PROCESS_NOT_FULLY_EXITED | 7 | The previous application process has not fully exited. |

## HyperSnapErrorInfo

Describes the error information of fast startup.

**Since:** 26.0.1

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model Constraint:** This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| code | [HyperSnapErrorCode](#hypersnaperrorcode) | No | No | Error code. |
| msg | string | No | No | Error message indicating the cause of the fast startup failure. |
| occurTimeStamp | number | No | No | Timestamp when the error occurs, that is, the time elapsed since the Unix epoch (1970-01-01 00:00:00 UTC), in milliseconds, as an integer. |

## hyperSnapManager.setHyperSnapEnabled

setHyperSnapEnabled(enableFlag: boolean): void

Enables or disables the Quick Launch feature of an app.

> **NOTE**
>
> - When this API is used to enable the app fast startup function, the system ultimately decides whether to create or use fast startup based on application compatibility, resource availability, and system policies. When this API is used to disable the fast startup function, it is guaranteed that the system will not create fast startup.
> - The configured value persists after a restart.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| enableFlag | boolean | Yes | Whether to enable the quick start feature. <br>- `true`: enables the application quick start feature (the system makes the final decision on whether to create quick start). <br>- `false`: disables the application quick start feature. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 16000150 | Failed to send request to system service. |

**Example**

```ts
import { hyperSnapManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Enable the app fast startup function.
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

Requests re-initialization of Quick Launch.

This method destroys the Quick Launch data that has been initialized in the current process, and the system will re-initialize Quick Launch at an appropriate time.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction:** This API can be used only in the stage model.

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 16000150 | Failed to send request to system service. |

**Example**

```ts
import { hyperSnapManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Request to reinitialize app fast startup.
  hyperSnapManager.requestRebuildHyperSnap();
  console.info('Requested to rebuild Hyper Snap successfully.');
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to request Hyper Snap rebuild. Code: ${code}, Message: ${message}`);
}
```

## hyperSnapManager.getLastError

getLastError(errType: HyperSnapErrorType): Promise&lt;HyperSnapErrorInfo&gt;

Obtains the last fast startup error information of the current application in the specified scenario.

> **NOTE**
>
> - The error information of each scenario is stored independently and does not affect each other. The stored error information of a scenario is cleared after a subsequent fast startup operation succeeds.
> - After the device restarts, all error information is cleared.
> - If no error has occurred in the specified scenario, the value of code in the returned errorInfo is ERR_OK, and the value of occurTimeStamp is 0.
> - Only the last fast startup related error of the application is retained, regardless of which snapshot it belongs to.

**Since:** 26.0.1

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| errType | [HyperSnapErrorType](#hypersnaperrortype) | Yes | Type of the fast startup error. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[HyperSnapErrorInfo](#hypersnaperrorinfo)&gt; | Promise used to return the last fast startup error information of the current application in the specified scenario. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 16000050 | Connect to system service failed. |

**Example**

```ts
import { hyperSnapManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Query the last error information in the snapshot creation scenario.
try {
  hyperSnapManager.getLastError(hyperSnapManager.HyperSnapErrorType.CREATE_SNAPSHOT)
    .then((errInfo: hyperSnapManager.HyperSnapErrorInfo) => {
      if (errInfo.code === hyperSnapManager.HyperSnapErrorCode.ERR_OK) {
        console.info('No Hyper Snap error occurred.');
        return;
      }
      console.info(`Last error code: ${errInfo.code}, msg: ${errInfo.msg}, occurTimeStamp: ${errInfo.occurTimeStamp}`);
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to get last error. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to get last error. Code: ${code}, Message: ${message}`);
}
```
