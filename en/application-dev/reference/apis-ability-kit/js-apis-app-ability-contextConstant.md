# @ohos.app.ability.contextConstant (Context-related Constants)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy; @yangxuguang-huawei; @Luobniz21-->
<!--Designer: @ccllee1; @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9b45198dbdb6f53f8bf0896d62425626f2442690 translatedAt=2026-09-03T10:13:22.629Z pushedAt=2026-09-05T10:47:30.370Z -->

ContextConstant provides Context-related enums, including the file encryption area level and process mode. The file encryption area level is used to protect application data security, and developers can select an appropriate encryption level based on application requirements. The process mode is used to control the startup mode and process behavior of a UIAbility. These enums help developers implement more flexible application architectures and more secure data management.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { contextConstant } from '@kit.AbilityKit';
```

## AreaMode

Enumerates the file encryption area levels to ensure data security in different scenarios. Developers can select an appropriate encryption level based on application requirements.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Value| Description                                                                                                                  |
|-----| -------- |----------------------------------------------------------------------------------------------------------------------|
| EL1 | 0 | Device-level encryption. Directories with this encryption level are accessible after the device is powered on.<br>**Atomic service API**: This API can be used in atomic services since API version 11.   |
| EL2 | 1 | User-level encryption. Directories with this encryption level are accessible only after the device is powered on and the password is entered (for the first time).<br>**Atomic service API**: This API can be used in atomic services since API version 11.      |
| EL3<sup>11+</sup> | 2 | User-level encryption area. The file permissions in different scenarios are as follows:<br/>Opened file: when locked, readable and writable; after unlocking, readable and writable.<br/>Unopened file: when locked, cannot be opened, not readable or writable; after unlocking, can be opened, readable and writable.<br/>Create a new file: when locked, can be created, can be opened, writable but not readable; after unlocking, can be created, can be opened, readable and writable.<br/>**Atomic service API**: Since API version 11, this API is supported in atomic services. |
| EL4<sup>11+</sup> | 3 | User-level encryption area. The file permissions in different scenarios are as follows:<br/>Opened file: when locked, not readable or writable; after unlocking, readable and writable.<br/>Unopened file: when locked, cannot be opened, not readable or writable; after unlocking, can be opened, readable and writable.<br/>Create a new file: when locked, cannot be created; after unlocking, can be created, can be opened, readable and writable.<br/>**Atomic service API**: Since API version 11, this API is supported in atomic services.  |
| EL5<sup>12+</sup> | 4 | Application-level encryption area. The file permissions in different scenarios are as follows:<br/>Opened file: when locked, readable and writable; after unlocking, readable and writable.<br/>Unopened file: when locked, after calling the [Access](js-apis-screenLockFileManager.md#screenlockfilemanageracquireaccess) API to obtain the retained key, can be opened, readable and writable; otherwise, cannot be opened, not readable or writable; after unlocking, can be opened, readable and writable.<br/>Create a new file: when locked, can be created, can be opened, readable and writable; after unlocking, can be created, can be opened, readable and writable.<br/>**Atomic service API**: Since API version 12, this API is supported in atomic services. |


## ProcessMode<sup>12+</sup>

Enumerates the process modes after a UIAbility is started, which are used to specify that the UIAbility is started in a new process and bound to a specified object (such as a parent process or a status bar icon).

As a property of [StartOptions](js-apis-app-ability-startOptions.md), **ProcessMode** takes effect only in [UIAbilityContext.startAbility](js-apis-inner-application-uiAbilityContext.md#startability-1) and is used to specify the process mode of the target UIAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences:** This feature takes effect only on PC, 2-in-1 and tablet devices. On other device types, it returns error code 801.

| Name | Value| Description                                                                                                                  |
|-----| -------- |----------------------------------------------------------------------------------------------------------------------|
| NEW_PROCESS_ATTACH_TO_PARENT | 1 | Creates a new process and starts the UIAbility in this process. This process exits along with the parent process (the caller process). That is, when the parent process exits, this process also exits automatically.<br>**Constraint**<br>To use this mode, require the target UIAbility to be in the same application with the caller.                     |
| NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM | 2 | A new process is created, the UIAbility is started on the process, and the process is bound to the status bar icon.<br>**Constraints**:<br>In this mode, the target UIAbility and caller must be in the same application, and the application must have an icon in the status bar.                 |
| ATTACH_TO_STATUS_BAR_ITEM | 3 | The UIAbility is started, and the process of the UIAbility is bound to the status bar icon.<br>**Constraints**:<br>In this mode, the target UIAbility and caller must be in the same application, and the application must have an icon in the status bar.                 |

**Example**

  ```ts
  import { UIAbility, Want, StartOptions, contextConstant } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  export default class EntryAbility extends UIAbility {
    onForeground() {
      // Construct the Want object and specify the target UIAbility information.
      let want: Want = {
        deviceId: '',
        bundleName: 'com.example.myapplication',
        abilityName: 'MainAbility2'
      };
    // Create the startup options and set the process mode and startup visibility.
    let options: StartOptions = {
          processMode: contextConstant.ProcessMode.NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM,
          startupVisibility: contextConstant.StartupVisibility.STARTUP_HIDE
        };

      try {
        // Start the target UIAbility.
        this.context.startAbility(want, options, (err: BusinessError) => {
          if (err.code) {
            // Process service logic errors.
            console.error(`startAbility failed, code is ${err.code}, message is ${err.message}`);
            return;
          }
          // Carry out normal service processing.
          console.info('startAbility succeed');
        });
      } catch (err) {
        // Process input parameter errors.
        let code = (err as BusinessError).code;
        let message = (err as BusinessError).message;
        console.error(`startAbility failed, code is ${code}, message is ${message}`);
      }
    }
  }
  ```

## StartupVisibility<sup>12+</sup>

Enumerates the visibility statuses of the UIAbility after it is started.

If the target UIAbility is set to invisible, the window of the target UIAbility is not displayed in the foreground, there is no icon in the dock, and the **onForeground** lifecycle of the target UIAbility is not triggered.

As a property of [StartOptions](js-apis-app-ability-startOptions.md), **StartupVisibility** takes effect only in [UIAbilityContext.startAbility](js-apis-inner-application-uiAbilityContext.md#startability-1) and specifies the visibility of the target UIAbility after it is started.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences:** This feature takes effect only on PC, 2-in-1 and tablet devices. On other device types, it returns error code 801.

| Name | Value| Description                                                                                                                  |
|-----| -------- |----------------------------------------------------------------------------------------------------------------------|
| STARTUP_HIDE | 0 | The target UIAbility is hidden after it is started in the new process. The **onForeground** lifecycle of the UIAbility is not invoked.       |
| STARTUP_SHOW | 1 | The target UIAbility is displayed normally after it is started in the new process.    |

**Example**

  See [ContextConstant.ProcessMode](#processmode12).

## Scenarios<sup>20+</sup>

Enumerates the scenarios where the [onNewWant](./js-apis-app-ability-uiAbility.md#onnewwant) lifecycle callback is not triggered. It is used in the [setOnNewWantSkipScenarios](./js-apis-inner-application-uiAbilityContext.md#setonnewwantskipscenarios20) API.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name | Value| Description                                                                                                                  |
|-----| -------- |----------------------------------------------------------------------------------------------------------------------|
| SCENARIO_MOVE_MISSION_TO_FRONT | 0x00000001 | <!--RP1-->A scenario where the system API [missionManager.moveMissionToFront](./js-apis-app-ability-missionManager-sys.md#missionmanagermovemissiontofront-2) is called to move the UIAbility to the foreground.<!--RP1End-->        |
| SCENARIO_SHOW_ABILITY | 0x00000002 | A scenario where the [showAbility](./js-apis-inner-application-uiAbilityContext.md#showability12) API is called to move the UIAbility to the foreground.    |
| SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT | 0x00000004 | A scenario where the [backToCallerAbilityWithResult](./js-apis-inner-application-uiAbilityContext.md#backtocallerabilitywithresult12) API is called to move the UIAbility to the foreground.    |

**Example**

```ts
import { AbilityConstant, contextConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    // Set the scenarios that do not trigger onNewWant, and combine multiple scenario flags.
    let scenarios: number = contextConstant.Scenarios.SCENARIO_MOVE_MISSION_TO_FRONT |
      contextConstant.Scenarios.SCENARIO_SHOW_ABILITY |
      contextConstant.Scenarios.SCENARIO_BACK_TO_CALLER_ABILITY_WITH_RESULT;

    try {
      // Set the scenarios that skip onNewWant.
      this.context.setOnNewWantSkipScenarios(scenarios).then(() => {
        // Carry out normal service processing.
        console.info('setOnNewWantSkipScenarios succeed');
      }).catch((err: BusinessError) => {
        // Process service logic errors.
        console.error(`setOnNewWantSkipScenarios failed, code is ${err.code}, message is ${err.message}`);
      });
    } catch (err) {
      // Process input parameter errors.
      let code = (err as BusinessError).code;
      let message = (err as BusinessError).message;
      console.error(`setOnNewWantSkipScenarios failed, code is ${code}, message is ${message}`);
    }
  }
}
```

## ContextType

Enumerates the common context types, used by the [isContextOf](./js-apis-inner-application-context.md#iscontextof) API.

**Since**: 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name  | Value | Description                                                                                                                   |
|-----| -------- |----------------------------------------------------------------------------------------------------------------------|
| APPLICATION_CONTEXT | 0 | Type of [ApplicationContext](js-apis-inner-application-applicationContext.md), which provides application-level resources and capabilities.  |
| ABILITY_STAGE_CONTEXT | 1 | Type of [AbilityStageContext](js-apis-inner-application-abilityStageContext.md), which provides module-level resources and capabilities.   |
| UIABILITY_CONTEXT | 2 | Type of [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md), which provides capabilities such as UI interaction and component startup.     |
| FORM_EXTENSION_CONTEXT | 3 | Type of [FormExtensionContext](../apis-form-kit/js-apis-inner-application-formExtensionContext.md), which provides card service capabilities.     |
| APP_SERVICE_EXTENSION_CONTEXT | 4 | Type of [AppServiceExtensionContext](js-apis-inner-application-appServiceExtensionContext.md), which provides background service capabilities.     |

**Example**

```ts
import { UIAbility, contextConstant } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    hilog.info(0x0000, 'testTag', `%{public}s`, 'Ability onCreate');
    // Check whether the context type is UIAbilityContext.
    let result = this.context.isContextOf(contextConstant.ContextType.UIABILITY_CONTEXT);
    hilog.info(0x0000, 'testTag', `match contextType result is:%{public}s`, JSON.stringify(result));
  }
}
```