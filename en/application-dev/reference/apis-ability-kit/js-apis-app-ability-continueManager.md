# @ohos.app.ability.continueManager (Cross-Device Migration)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=12692091655ba228529ead0007e1919066cc3dae translatedAt=2026-09-03T10:13:48.591Z pushedAt=2026-09-05T10:47:30.374Z -->

continueManager (cross-device migration) provides the management capability for cross-device migration of applications, for example, obtaining the result of quickly starting the target application during cross-device migration. Cross-device migration means that when a user operates an application on one device, the user can quickly switch to the same application on another device and seamlessly continue the application experience from the previous device. Specifically, during use, when the usage scenario changes - the previously used device is no longer suitable for continuing the current task, or a more suitable device is available nearby - the user can choose to use a new device to continue the current task. After cross-device migration is complete, the application on the previous device can exit or remain, and the user can focus on the started device to continue the task.<!--Del-->For details about the design logic and implementation mechanism, see [cross-device migration](../../application-models/hop-cross-device-migration.md).<!--DelEnd-->

> **NOTE**
> 
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { continueManager } from '@kit.AbilityKit';
```

## continueManager.on

on(type: 'prepareContinue', context: Context, callback: AsyncCallback\<ContinueResultInfo>): void

Registers a callback function to obtain the result when an application is quickly started. This API uses an asynchronous callback to return the result.

Applies to cross-device application migration scenarios, such as migrating game progress from a phone to a tablet, cross-device video playback synchronization, and document editing collaboration, where application state continuity must be maintained.

> **NOTE**
>
> The quick start feature allows the application to start concurrently while the user triggers migration and waits for the migration data to return, reducing wait time. To enable the quick start feature, add the "_ContinueQuickStart" suffix to the value of the continueType tag in the [module.json5 configuration file](../../quick-start/module-configuration-file.md) of the source application.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** When this API is called on a Wearable device that does not support distributed services, error code 16300501 is returned.

**Parameters**

  | Name| Type                                                                                             | Mandatory| Description                                      |
  | -------- |-------------------------------------------------------------------------------------------------| -------- |------------------------------------------|
  | type | string                                                                                          | Yes| The value is fixed at **prepareContinue**.                    |
  | context | [Context](../apis-ability-kit/js-apis-inner-application-baseContext.md)                                                                                         | Yes | Context of the Ability (application component).                         |
  | callback | AsyncCallback&lt;[ContinueResultInfo](js-apis-app-ability-continueManager.md#continueresultinfo)&gt; | Yes | Callback function. When the quick start result is obtained successfully, err is undefined and ContinueResultInfo is the obtained quick start result. Otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Distributed Scheduler Error Codes](errorcode-DistributedSchedule.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 16300501 | the system ability work abnormally. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, continueManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[MigrationAbility]';
const DOMAIN_NUMBER: number = 0xFF00;

export default class MigrationAbility extends UIAbility {

    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        hilog.info(DOMAIN_NUMBER, TAG, '%{public}s', 'Ability onCreate');

        // 1. Quick start is configured. Trigger the lifecycle callback when the application is launched immediately.
        if (launchParam.launchReason === AbilityConstant.LaunchReason.PREPARE_CONTINUATION) {
            // Register the callback to obtain the quick start result.
            try {
              continueManager.on('prepareContinue', this.context, (err, continueResultInfo) => {
                if (err.code != 0) {
                  hilog.error(DOMAIN_NUMBER, TAG, 'register failed, cause: %{public}s', JSON.stringify(err));
                  return;
                }
                hilog.info(DOMAIN_NUMBER, TAG, 'register finished, %{public}s', JSON.stringify(continueResultInfo));
              });
            } catch (e) {
              hilog.error(DOMAIN_NUMBER, TAG, 'register failed, cause: %{public}s', JSON.stringify(e));
            }
            // If the migration data is large, add a loading page here (displaying a loading indicator, etc.).
            // Handle custom application redirection, timing, and other issues.
            // ...
        }
    }
}
```

## continueManager.off

off(type: 'prepareContinue', context: Context, callback?: AsyncCallback\<ContinueResultInfo>): void

Unregisters the callback function when an application is quickly started. After successful unregistration, notifications of the quick start result are no longer received. This API uses an asynchronous callback to return the result.

Applies to callback cleanup scenarios after cross-device application migration is complete or canceled, such as clearing listeners after successful application migration and releasing resources when the user cancels the migration operation.

> **NOTE**
>
> The quick start feature allows the application to start concurrently while the user triggers migration and waits for the migration data to return, reducing wait time. To enable the quick start feature, add the "_ContinueQuickStart" suffix to the value of the continueType tag in the [module.json5 configuration file](../../quick-start/module-configuration-file.md) of the source application.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name| Type                                | Mandatory| Description                                  |
| -------- |------------------------------------| -------- |--------------------------------------|
| type | string                             | Yes| The value is fixed at **prepareContinue**.                |
| context | [Context](../apis-ability-kit/js-apis-inner-application-baseContext.md) | Yes | Context of the Ability (application component). |
| callback | AsyncCallback&lt;[ContinueResultInfo](js-apis-app-ability-continueManager.md#continueresultinfo)&gt; | No | Callback function. If the callback function is unregistered successfully, err is undefined and ContinueResultInfo is the obtained unregistration result of the callback function. Otherwise, it is an error object. If this parameter is not specified, all registered callbacks are unregistered; if it is specified, only the specified callback function is unregistered. |

**Error codes**

For details about the error codes, see [Distributed Scheduler Error Codes](errorcode-DistributedSchedule.md).

| ID   | Error Message|
|----------| -------------------------------- |
| 16300501 | the system ability work abnormally. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, continueManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG: string = '[MigrationAbility]';
const DOMAIN_NUMBER: number = 0xFF00;

export default class MigrationAbility extends UIAbility {

    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        hilog.info(DOMAIN_NUMBER, TAG, '%{public}s', 'Ability onCreate');

        // 1. Quick start is configured. Trigger the lifecycle callback when the application is launched immediately.
        if (launchParam.launchReason === AbilityConstant.LaunchReason.PREPARE_CONTINUATION) {
            // Unregister the callback used to obtain the quick start result.
            try {
              continueManager.off('prepareContinue', this.context, (err, continueResultInfo) => {
                if (err.code != 0) {
                  hilog.error(DOMAIN_NUMBER, TAG, 'unregister failed, cause: %{public}s', JSON.stringify(err));
                  return;
                }
                hilog.info(DOMAIN_NUMBER, TAG, 'unregister finished, %{public}s', JSON.stringify(continueResultInfo));
              });
            } catch (e) {
              hilog.error(DOMAIN_NUMBER, TAG, 'unregister failed, cause: %{public}s', JSON.stringify(e));
            }
            // If the application migration data is large, add a loading page here (displaying a loading indicator, etc.).
            // Handle issues such as custom application redirection and timing.
            // ...
        }
    }
}
```

## ContinueResultInfo

Defines the quick start result returned by registering or unregistering a callback function, including the operation status code and result description information, which is used by applications to obtain the execution result of cross-device migration quick start.

**Model restriction:** This API can be used only in the stage model.

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name| Type                                                                           | Read-Only| Optional| Description      |
| -------- |-------------------------------------------------------------------------------|----|----|----------|
| resultState | [ContinueStateCode](js-apis-app-ability-continueManager.md#continuestatecode) | No  | No  | Result status code of the operation. |
| resultInfo | string                                                                        | No  | Yes  | Description of the operation result, providing detailed information about the success or failure of the operation. |

## ContinueStateCode

Enumerates the status codes of the quick start result.

**Model restriction:** This API can be used only in the stage model.

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.


**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

| Name| Value | Description   |
| -------- |----|-------|
| SUCCESS  | 0  | Operation succeeded. Indicates that the quick start has been completed, and the application can proceed with the cross-device migration process. |
| SYSTEM_ERROR | 1 | Operation failed. Indicates that a system error occurred during the quick start. The application needs to notify the user that the migration failed and decide whether to retry based on the service scenario. |
