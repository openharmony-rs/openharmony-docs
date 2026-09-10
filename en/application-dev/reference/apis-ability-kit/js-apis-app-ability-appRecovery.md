# @ohos.app.ability.appRecovery (Application Recovery)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1d900df92d6661ea579d9ba078f8fe29054d3394 translatedAt=2026-09-03T09:57:50.559Z pushedAt=2026-09-05T10:47:30.229Z -->

The appRecovery module provides the capability of recovering apps in faulty states. Since API version 11, app self-recovery is supported in the app crash (JS_CRASH) and app freeze (APP_FREEZE) fault scenarios. Since API version 24, app self-recovery is supported in the process crash (CPP_CRASH) fault scenario. In addition, app state saving and recovery are supported to help developers improve app stability.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> In API version 9, only app recovery for a single ability in a single process is supported.
>
> In API version 10, the scenario where a process contains multiple abilities is supported.
>
> In API version 24, app recovery upon CPP_CRASH is supported.

## Modules to Import
```ts
import { appRecovery } from '@kit.AbilityKit';
```

## RestartFlag

Enumerates the application restart flags. This enum is used as an input parameter of [enableAppRecovery](#apprecoveryenableapprecovery).


**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name      | Value  | Description      |
| ---------- | ---- | ---------- |
| ALWAYS_RESTART   | 0    | Always restarts the application. <br>**Atomic service API**: This API is supported in atomic services since API version 11.|
| RESTART_WHEN_JS_CRASH   | 0x0001    | Restarts the application when a JS_CRASH occurs.<br>**Atomic service API**: This API is supported in atomic services since API version 11. |
| RESTART_WHEN_APP_FREEZE   | 0x0002    | Restarts the application when an APP_FREEZE occurs.<br>**Atomic service API**: This API is supported in atomic services since API version 11. |
| RESTART_WHEN_CPP_CRASH<sup>24+</sup>    | 0x0004    | Restarts the application when a CPP_CRASH occurs.<br>**Model restriction**: This API can be used only in the stage model.<br>**Atomic service API**: This API is supported in atomic services since API version 24.|
| NO_RESTART           | 0xFFFF    | Never restarts the application.<br>**Atomic service API**: This API is supported in atomic services since API version 11. |

## SaveOccasionFlag

Enumerates the scenarios for saving the application state. This enum is used as an input parameter of [enableAppRecovery](#apprecoveryenableapprecovery).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                         | Value  | Description                                                        |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| SAVE_WHEN_ERROR            | 0x0001    | Saving the application state when an application fault occurs.|
| SAVE_WHEN_BACKGROUND            | 0x0002    | Saving the application state when the application is switched to the background.|

## SaveModeFlag

Enumerates the application state saving modes. This enum is used as an input parameter of [enableAppRecovery](#apprecoveryenableapprecovery).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                         | Value  | Description                                                        |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| SAVE_WITH_FILE             | 0x0001    | The application state is saved and written to the local file cache.|
| SAVE_WITH_SHARED_MEMORY             | 0x0002    | The application state is saved in the memory. When the application exits due to a fault, it is written to the local file cache.|

## appRecovery.enableAppRecovery

enableAppRecovery(restart?: [RestartFlag](#restartflag), saveOccasion?: [SaveOccasionFlag](#saveoccasionflag), saveMode?: [SaveModeFlag](#savemodeflag)) : void

Enables application recovery. After this API is called, the first ability that is displayed when the application is started from the initiator can be restored.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| restart | [RestartFlag](#restartflag) | No | Enum type, indicating whether to restart the app when the corresponding fault occurs. The default value is ALWAYS_RESTART, which means the app is always restarted. |
| saveOccasion | [SaveOccasionFlag](#saveoccasionflag) | No | Enum type, used to specify the trigger condition for state saving. The default value is SAVE_WHEN_ERROR, which means the state is saved when an app fault occurs. |
| saveMode | [SaveModeFlag](#savemodeflag) | No | Enum type, used to specify the implementation mode of state saving. The default value is SAVE_WITH_FILE, which means each state saving is written to the local file cache. |

**Example**

```ts
import { appRecovery, AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    appRecovery.enableAppRecovery(
      appRecovery.RestartFlag.ALWAYS_RESTART,
      appRecovery.SaveOccasionFlag.SAVE_WHEN_ERROR,
      appRecovery.SaveModeFlag.SAVE_WITH_FILE
    );
  }
}
```

## appRecovery.restartApp

restartApp(): void

Restarts the current process and starts the first ability that is displayed when the application is started. If the state of this ability is saved, the saved state data is passed into the **wantParam** property in the **want** parameter of the **onCreate** lifecycle callback of the ability.

Since API version 10, the ability specified by [setRestartWant](#apprecoverysetrestartwant10) is started. If no ability is specified, the following rules are used:

If the ability of the current application running in the foreground supports recovery, that ability is started.

If multiple abilities that support recovery is running in the foreground, only the last ability is started.

If no ability is running in the foreground, none of them is started.

This API can be used together with the APIs of [errorManager](js-apis-app-ability-errorManager.md). The interval between two restarts must be greater than one minute. If this API is called repeatedly within one minute, the application exits but does not restart. The behavior of automatic restart is the same as that of proactive restart.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core


**Example**

```ts
import { appRecovery, errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    console.error('onUnhandledException, errorMsg: ', errorMsg);
    appRecovery.restartApp();
  }
};

try {
  errorManager.on('error', observer);
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```

## appRecovery.saveAppState

saveAppState(): boolean

Saves the state data of the current app (including the state information of abilities), which will be used when the app is recovered. This API can be used in conjunction with the related APIs of [errorManager](js-apis-app-ability-errorManager.md).

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Whether the application state is saved. **true** if saved, **false** otherwise.|

**Example**

```ts
import { appRecovery, errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    console.error('onUnhandledException, errorMsg: ', errorMsg);
    appRecovery.saveAppState();
  }
};

try {
  errorManager.on('error', observer);
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```

## appRecovery.saveAppState<sup>10+</sup>

saveAppState(context?: UIAbilityContext): boolean

Saves the ability state, which will be used for recovery. This API can be used together with the APIs of [errorManager](js-apis-app-ability-errorManager.md).

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md)| No| Context of the target ability.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Whether the application state is saved. **true** if saved, **false** otherwise.|

**Example**

```ts
import { appRecovery, errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    console.error('onUnhandledException, errorMsg: ', errorMsg);
    // context is the context of the UIAbility instance. Use an arrow function or save it in advance outside the callback.
    appRecovery.saveAppState(this.context);
  }
};

try {
  errorManager.on('error', observer);
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```

## appRecovery.setRestartWant<sup>10+</sup>

setRestartWant(want: Want): void

Sets the ability to be started for the next app recovery. The ability must be a UIAbility in the current bundle. When the app is recovered through the [restartApp](#apprecoveryrestartapp) method or app fault recovery, the ability set here will be launched.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| want | [Want](js-apis-app-ability-want.md)| Yes | Specifies the ability to be restarted and recovered by setting the "bundleName" and "abilityName" fields in Want. It must be used in conjunction with the enableAppRecovery API to set an appropriate RestartFlag to determine when to trigger the restart. setRestartWant only specifies the ability to be launched for restart; whether to restart is determined by RestartFlag. |

**Example**

```ts
import { appRecovery, Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  build() {
    Button("Start to Recover Ability")
      .fontSize(40)
      .fontWeight(FontWeight.Bold)
      .onClick(() => {
        // set restart want
        let want: Want = {
          bundleName: "ohos.samples.recovery",
          abilityName: "RecoveryAbility"
        };

        appRecovery.setRestartWant(want);
      })
  }
}
```