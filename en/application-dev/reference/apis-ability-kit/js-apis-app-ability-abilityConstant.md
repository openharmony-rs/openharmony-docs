# @ohos.app.ability.AbilityConstant (Ability-related Constants)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @littlejerry1-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=17d3b236d2c2a3bbfc7bc46d7fe0f1415b7b5049 translatedAt=2026-09-03T09:52:54.492Z pushedAt=2026-09-07T03:53:47.957Z -->

AbilityConstant provides enums related to abilities, including application launch reasons ([LaunchReason](#launchreason)), last exit reasons ([LastExitReason](#lastexitreason)), and migration results ([OnContinueResult](#oncontinueresult)).

> **NOTE**
> 
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { AbilityConstant } from '@kit.AbilityKit';
```

## Constants

**System capability**: SystemCapability.Ability.AbilityBase

**Atomic service API**: This API can be used in atomic services since API version 20.

| Name| Type| Value| Description|
| ---- | -----| ---- | ---------------------------------------------------------- |
| REASON_MESSAGE_DESKTOP_SHORTCUT<sup>20+</sup>  | string | "ReasonMessage_DesktopShortcut" | The UIAbility is launched via a home screen shortcut. If this string is obtained from the **launchReasonMessage** property in [LaunchParam](#launchparam), the UIAbility is initiated by touching a shortcut on the home screen.|

## LaunchParam

Describes the launch parameters, which mainly include the ability launch reasons and reasons for the last exit. The parameter values are automatically passed in by the system when the ability is launched. You do not need to change the values.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| launchReason | [LaunchReason](#launchreason)| No| No| An enumerated value indicating the reason for ability launch (for example, recovery from a fault, intent invocation, or atomic service sharing). For details, see [LaunchReason](#launchreason).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| launchReasonMessage<sup>18+</sup> | string | No| Yes| Detailed message that describes the reason for the ability launch.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| lastExitReason | [LastExitReason](#lastexitreason) | No| No| An enumerated value indicating the reason for the last exit of the ability.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| lastExitMessage<sup>12+</sup> | string | No| No| Detailed message that describes the reason for the last exit of the ability.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| lastExitDetailInfo<sup>18+</sup> | [LastExitDetailInfo](#lastexitdetailinfo18) | No| Yes| Key runtime information for the last exit of the ability (including process ID, exit timestamp, and RSS memory value).<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| launchUTCTime<sup>23+</sup> | number | No| Yes| UTC timestamp when the UIAbility starts, in milliseconds.<br>**Atomic service API**: This API can be used in atomic services since API version 23.<br>**Constraints**:<br>This feature takes effect only when the UIAbility is started. For other types of abilities (for example, UIExtensionAbility), the obtained start time is the default value **0**.|
| launchUptime<sup>23+</sup> | number | No| Yes| System uptime (the time elapsed since the system booted up) when the UIAbility starts, in milliseconds.<br>**Atomic service API**: This API can be used in atomic services since API version 23.<br>**Constraints**:<br>This feature takes effect only when the UIAbility is started. For other types of abilities (for example, UIExtensionAbility), the obtained start time is the default value **0**.|

## LaunchReason

Enumerates the ability launch reasons. You can use it together with the value of **launchParam.launchReason** in [onCreate(want, launchParam)](js-apis-app-ability-uiAbility.md#oncreate) of the UIAbility to complete different operations.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                         | Value  | Description                                                        |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| UNKNOWN          | 0    | Unknown reason.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| START_ABILITY          | 1    | The ability is started by calling [startAbility](js-apis-inner-application-uiAbilityContext.md#startability).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| CALL | 2    | The ability is started by calling [startAbilityByCall](js-apis-inner-application-uiAbilityContext.md#startabilitybycall).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| CONTINUATION           | 3    | The ability is started by means of cross-device migration.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| APP_RECOVERY           | 4    | The ability is automatically started when the application is restored from a fault.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| SHARE<sup>10+</sup>           | 5    | The ability is started by means of atomic service sharing.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| AUTO_STARTUP<sup>11+</sup>           | 8    | The ability is automatically started upon system boot.|
| INSIGHT_INTENT<sup>11+</sup>           | 9    | The ability is started by the InsightIntent framework.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| PREPARE_CONTINUATION<sup>12+</sup>           | 10    | The ability is started in advance during cross-device migration.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| PRELOAD<sup>20+</sup>           | 11    | The ability is started through preloading.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

**Example**

```ts
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    if (launchParam.launchReason === AbilityConstant.LaunchReason.START_ABILITY) {
      console.info('The ability has been started by the way of startAbility.');
    }
  }
}
```

## LastExitReason

Enumerates the reasons for the last exit of the ability. You can use it together with the value of **launchParam.lastExitReason** in [onCreate()](js-apis-app-ability-uiAbility.md#oncreate) of the UIAbility to complete different operations.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                         | Value  | Description                                                        |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| UNKNOWN          | 0    | Unknown reason.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| ABILITY_NOT_RESPONDING<sup>(deprecated)</sup> | 1    | The Ability component does not respond.<br>**Note:** Supported since API version 9 and deprecated since API version 10. Use APP_FREEZE instead.|
| NORMAL | 2    | The user proactively closes the application, and the application exits normally.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Note:** When the developer directly calls [process.exit()](../apis-arkts/js-apis-process.md#processexitdeprecated), the kernel kill command, or other capabilities not provided by Ability Kit to forcibly terminate the application process, NORMAL is also returned. |
| CPP_CRASH<sup>10+</sup>  | 3    | The ability exits due to [process crash](../../dfx/cppcrash-guidelines.md).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| JS_ERROR<sup>10+</sup>  | 4    | The ability exits due to a JS_ERROR fault triggered when an application has a JS syntax error that is not captured by developers.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| APP_FREEZE<sup>10+</sup>  | 5    | The ability exits due to [application freeze](../../dfx/appfreeze-guidelines.md).<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| PERFORMANCE_CONTROL<sup>10+</sup>  | 6    | The ability exits due to system performance problems, for example, insufficient device memory.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>Note: This API will be deprecated. You are advised to use **RESOURCE_CONTROL** instead.|
| RESOURCE_CONTROL<sup>10+</sup>  | 7    | The application exits due to improper use of system resources. The specific error cause can be obtained through [LaunchParam.lastExitMessage](#launchparam). Possible causes are as follows: <br> - CPU Highload, high CPU load.<br> - CPU_EXT Highload, fast CPU load detection.<br> - IO Manage Control, I/O control.<br> - App Memory Deterioration, application memory over-limit deterioration.<br> - Temperature Control, temperature control.<br> - Memory Pressure, low memory of the entire device triggers process termination by priority from low to high.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| UPGRADE<sup>10+</sup>  | 8    | The application exits due to an upgrade.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| USER_REQUEST<sup>18+</sup>  | 9    | The ability exits because it receives a request from the multitasking center.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| SIGNAL<sup>18+</sup>  | 10    | The ability exits because it receives a kill signal from the system.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|

**Example**

```ts
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    if (launchParam.lastExitReason === AbilityConstant.LastExitReason.APP_FREEZE) {
      console.info('The ability has exited last because the ability was not responding.');
    }
    if (launchParam.lastExitReason === AbilityConstant.LastExitReason.RESOURCE_CONTROL) {
      console.info(`The ability has exited last because the rss control, the lastExitReason is ${launchParam.lastExitReason}, the lastExitMessage is ${launchParam.lastExitMessage}.`);
    }
  }
}
```

## LastExitDetailInfo<sup>18+</sup>

Describes the key runtime information of the process where the ability last exited.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| pid | number | No| No| ID of the process where the ability last exited.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| processName | string | No| No| Name of the process.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| uid | number | No| No| UID of the application.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| exitSubReason | number | No| No| Specific reason for the last exit of the ability.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| exitMsg | string | No| No| Reason why the process was killed.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| rss | number | No| No| Actual memory usage of the process, in KB.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| pss | number | No| No| Actual physical memory usage of the process, in KB.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| timestamp | number | No| No| Exact time when the ability last exited.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| processState<sup>20+</sup> | [appManager.ProcessState](js-apis-app-ability-appManager.md#processstate10) | No| Yes| Process status of the ability when it last exited.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|
| killReason<sup>24+</sup> | string | No | Yes | Reason why the Ability last exited. For details about the values, see [reason field description of the app termination event](../../dfx/hiappevent-watcher-app-killed-events.md#reason).<br/>**Atomic service API**: Since API version 24, this API is supported in atomic services. |

> **NOTE**
>
> You are advised to use [App Killed](../../dfx/appkilled-guidelines.md) detection to obtain the information about abnormal application exit. It is no longer recommended to use exitSubReason to obtain the information.
>
> The values of exitSubReason are described as follows:
>
> - When [LastExitReason](#lastexitreason) is NORMAL:
>   - 9: The kernel forcibly terminates the process, with the termination signal SIGKILL.
>   - 15: The kernel forcibly terminates the process, with the termination signal SIGTERM.
>
> - When [LastExitReason](#lastexitreason) is PERFORMANCE_CONTROL:
>   - 100: The process is killed when entering outdoor mode.
>   - 101: The process is killed when exiting outdoor mode.
>   - 102: The process is killed in outdoor mode.
>   - 3000: The process is killed due to abnormal freeze control, where unreasonable subscriptions in the background cause callback wakeup.
>   - 3001: The process is killed due to abnormal freeze control, where unreasonable subscriptions in the background cause the application to hang when processing callbacks.
>   - 3002: The process is killed due to abnormal GNSS operation.
>   - 3003: The process is killed due to abnormal Bluetooth operation.
>   - 3004: The process is killed due to abnormal RunningLock holding.
>   - 3005: The process is killed due to abnormal kernel lock.
>   - 3006: The process is killed in power saving mode.
>   - 3007: The process is killed due to abnormal high power consumption of a module.
>   - 3042: The process is killed in emergency mode or super power saving mode. The specific error cause can be distinguished through [LaunchParam.lastExitMessage](#launchparam).
>
> - When [LastExitReason](#lastexitreason) is RESOURCE_CONTROL:
>   - 101: The application does not apply for a proper background task, but a large amount of audio is played in the background.
>   - 102: The application does not apply for a proper background task, but recording is performed in the background.
>   - 103: The application has a high CPU load in the background.
>   - 105: The application exceeds the I/O limit.
>   - 106: The process is killed due to ION memory leak control or malicious use of background tasks. The specific error cause can be distinguished through [LaunchParam.lastExitMessage](#launchparam).
>   - 107: The memory usage of the background application exceeds twice the detection threshold, with PSS accounting for the highest proportion.
>   - 108: The memory usage of the background application exceeds a specific threshold, with PSS accounting for the highest proportion.
>   - 110: The process is killed due to GPU memory leak control.
>   - 111: The process is killed due to VMA memory leak control.
>   - 112: The process is killed due to handle leak control.
>   - 113: The process is killed due to thread leak control.
>   - 114: The process is killed due to ASHMEM memory leak control.
>   - 117: The process is killed due to page table leak control.
>   - 301: The process is killed due to GPU memory exceeding the limit or thermal cleanup. The specific error cause can be distinguished through [LaunchParam.lastExitMessage](#launchparam).

**Example**

```ts
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    if (launchParam.lastExitDetailInfo) {
      console.info(`pid: ${launchParam.lastExitDetailInfo.pid}
      \n processName: ${launchParam.lastExitDetailInfo.processName}
      \n uid: ${launchParam.lastExitDetailInfo.uid}
      \n exitSubReason: ${launchParam.lastExitDetailInfo.exitSubReason}
      \n exitMsg: ${launchParam.lastExitDetailInfo.exitMsg}
      \n rss: ${launchParam.lastExitDetailInfo.rss}
      \n pss: ${launchParam.lastExitDetailInfo.pss}
      \n timestamp: ${launchParam.lastExitDetailInfo.timestamp}
      \n processState: ${launchParam.lastExitDetailInfo.processState}
      \n killReason: ${launchParam.lastExitDetailInfo?.killReason}.`
      );
    }
  }
}
```

## OnContinueResult

Enumerates the ability continuation results. You can use it in [onContinue()](js-apis-app-ability-uiAbility.md#oncontinue) of the UIAbility to complete different operations.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                         | Value  | Description                                                        |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| AGREE           | 0    | The ability continuation is accepted.|
| REJECT           | 1    | The ability continuation is rejected. If the application is abnormal in [onContinue](js-apis-app-ability-uiAbility.md#oncontinue), which results in abnormal display during data restoration, this result is returned.|
| MISMATCH  | 2    | The version does not match. The application on the initiator can obtain the version of the target application from [onContinue](js-apis-app-ability-uiAbility.md#oncontinue). If the ability continuation cannot be performed due to version mismatch, this result is returned.|

**Example**

```ts
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onContinue(wantParam: Record<string, Object>) {
    return AbilityConstant.OnContinueResult.AGREE;
  }
}
```

## MemoryLevel

Enumerates the memory levels of the entire device. You can use it in [onMemoryLevel()](js-apis-app-ability-ability.md#abilityonmemorylevel) of the UIAbility to complete different operations.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                        | Value| Description               |
| ---                         | --- | ---           |
| MEMORY_LEVEL_MODERATE       | 0   | Indicates that the system has a moderate amount of available memory. Due to differences in system-wide memory thresholds across devices, the actual performance may vary by product. For details, please refer to the notes below.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| MEMORY_LEVEL_LOW            | 1   | Indicates that the system has low available memory. Due to differences in system-wide memory thresholds across devices, the actual performance may vary by product. For details, please refer to the notes below.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| MEMORY_LEVEL_CRITICAL       | 2   | Indicates that the available memory of the entire device is extremely low. Due to different memory watermarks of the entire device, the behavior may vary on different products. For details, see the description below.<br>**Atomic service API**: This API is supported in atomic services since API version 11. |
| MEMORY_LEVEL_UI_HIDDEN<sup>24+</sup>      | 3   | Indicates that all UI of the application is invisible, and some resources should be released. This enum takes effect only for applications that switch from the foreground to the background.<br>**Atomic service API**: This API is supported in atomic services since API version 24.<br>**Constraints**: In actual scenarios, this memory level is triggered only on Phone devices. However, the [send-memory-level](../../tools/aa-tool.md#send-memory-level) debug command can trigger this memory level on all devices. |
| MEMORY_LEVEL_BACKGROUND_MODERATE<sup>24+</sup>     | 4   | Indicates that the application has just been used, that is, it is at the head of the least recently used (LRU) list, and will not be cleaned up by the system for the time being. This enum takes effect only for background applications.<br>**Atomic service API**: This API is supported in atomic services since API version 24.<br>**Constraints**: In actual scenarios, this memory level is triggered only on Phone devices. However, the [send-memory-level](../../tools/aa-tool.md#send-memory-level) debug command can trigger this memory level on all devices. |
| MEMORY_LEVEL_BACKGROUND_LOW<sup>24+</sup>    | 5   | Indicates that the application has not been used for a period of time, that is, it is in the middle of the least recently used (LRU) list, and is at risk of being cleaned up by the system. This enum takes effect only for background applications.<br>**Atomic service API**: This API is supported in atomic services since API version 24.<br>**Constraints**: In actual scenarios, this memory level is triggered only on Phone devices. However, the [send-memory-level](../../tools/aa-tool.md#send-memory-level) debug command can trigger this memory level on all devices. |
| MEMORY_LEVEL_BACKGROUND_CRITICAL<sup>24+</sup>    | 6   | Indicates that the application has not been used for a long time, that is, it is at the tail of the least recently used (LRU) list, and will be cleaned up by the system first. This enum takes effect only for background applications.<br>**Atomic service API**: This API is supported in atomic services since API version 24.<br>**Constraints**: In actual scenarios, this memory level is triggered only on Phone devices. However, the [send-memory-level](../../tools/aa-tool.md#send-memory-level) debug command can trigger this memory level on all devices. |

> **NOTE**
>
> - The trigger conditions may differ across various products. For example, on a standard device with 12 GB of memory:
>   - When the available memory of the entire device drops to 1700 MB to 1800 MB, the onMemoryLevel callback with the value 0 is triggered, indicating that the available memory of the entire device is moderate.
>   - When the available memory of the entire device drops to 1600 MB to 1700 MB, the onMemoryLevel callback with the value 1 is triggered, indicating that the available memory of the entire device is low.
>   - When the available memory of the entire device drops below 1600 MB, the onMemoryLevel callback with the value 2 is triggered, indicating that the available memory of the entire device is very low.
>
> - LRU: a linked list that sorts applications by their most recent usage order. The most recently used application is usually placed at the head of the linked list (front), and the least frequently used application is placed at the tail (back). When memory is insufficient, applications at the back are cleared first.
> - When the LRU changes, background applications trigger the onMemoryLevel callback of the corresponding MemoryLevel (MEMORY_LEVEL_BACKGROUND_MODERATE, MEMORY_LEVEL_BACKGROUND_LOW, and MEMORY_LEVEL_BACKGROUND_CRITICAL) based on their positions in the application usage sorting linked list (LRU). If an application is frozen, it receives the corresponding onMemoryLevel callback when it is woken up. Therefore, you are advised not to perform time-consuming operations in this callback.

**Example**

```ts
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onMemoryLevel(level: AbilityConstant.MemoryLevel) {
    if (level === AbilityConstant.MemoryLevel.MEMORY_LEVEL_CRITICAL) {
      console.info('The memory of device is critical, please release some memory.');
    }
  }
}
```

## WindowMode<sup>12+</sup>

Enumerates the window modes in which a UIAbility can be displayed at startup. You can use it in [startAbility](js-apis-inner-application-uiAbilityContext.md#startability-2).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                       | Value| Description                |
| ---                         | --- | ---                  |
| WINDOW_MODE_FULLSCREEN      | 1   | Full-screen mode. It takes effect only on 2-in-1 devices and tablets. |
| WINDOW_MODE_SPLIT_PRIMARY   | 100 | Supports setting the split-screen mode when an ability is started within the application, with the window on the left side of the split screen. This takes effect only on tablets, PCs/2-in-1 devices, and foldable devices that support a landscape home screen and are in the expanded state.   |
| WINDOW_MODE_SPLIT_SECONDARY | 101 | Supports setting the split-screen mode when an ability is started within the application, with the window on the right side of the split screen. This takes effect only on tablets, PCs/2-in-1 devices, and foldable devices that support a landscape home screen and are in the expanded state.   |
| WINDOW_MODE_SPLIT | 105 | Supports setting the split-screen mode when an ability is started within the application. The newly created window is displayed on the right side of the focused window by default. This takes effect only on foldable devices and tablets.<br>**Since:** 26.0.0   |

**Example**

```ts
import { UIAbility, StartOptions, Want, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let targetWant: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility'
};
let option: StartOptions = {
  windowMode: AbilityConstant.WindowMode.WINDOW_MODE_SPLIT_PRIMARY
};

// Ensure that the context is obtained.
export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    this.context.startAbility(targetWant, option).then(() => {
      console.info('Succeed to start ability.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to start ability with error: ${JSON.stringify(error)}`);
    });
  }
}
```

## OnSaveResult

Enumerates the result types for the operation of saving application data. You can use it in [onSaveState()](js-apis-app-ability-uiAbility.md#onsavestate) of the UIAbility to complete [UIAbility backup and restore](../../application-models/ability-recover-guideline.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                         | Value  | Description                                                        |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| ALL_AGREE           | 0    | Always agreed to save the status.|
| CONTINUATION_REJECT           | 1    | Rejected to save the status in continuation.|
| CONTINUATION_MISMATCH  | 2    | Continuation mismatch.|
| RECOVERY_AGREE           | 3    | Agreed to restore the saved status.|
| RECOVERY_REJECT  | 4    | Rejected to restore the saved status.|
| ALL_REJECT  | 5    | Always rejected to save the status.|

**Example**

```ts
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onSaveState(reason: AbilityConstant.StateType, wantParam: Record<string, Object>) {
    return AbilityConstant.OnSaveResult.ALL_AGREE;
  }
}
```

## StateType

Enumerates the scenarios for saving application data. You can use it in [onSaveState()](js-apis-app-ability-uiAbility.md#onsavestate) of the UIAbility to complete [UIAbility backup and restore](../../application-models/ability-recover-guideline.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                         | Value  | Description                                                        |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| CONTINUATION           | 0    | Application migration scenario.|
| APP_RECOVERY           | 1    | Application recovery scenario.|

**Example**

```ts
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onSaveState(reason: AbilityConstant.StateType, wantParam: Record<string, Object>) {
    if (reason === AbilityConstant.StateType.CONTINUATION) {
      console.info('Save the ability data when the ability is continuing.');
    }
    return AbilityConstant.OnSaveResult.ALL_AGREE;
  }
}
```

## ContinueState<sup>10+</sup>

Enumerates the mission continuation states of the application. It is used in the [setMissionContinueState](js-apis-inner-application-uiAbilityContext.md#setmissioncontinuestate10) API of [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

| Name          | Value      | Description                                                        |
| ------------- | --------- | ------------------------------------------------------------ |
| ACTIVE        | 0         | Mission continuation is activated for the current application.                             |
| INACTIVE      | 1         | Mission continuation is not activated for the current application.                           |

**Example**

```ts
import { UIAbility, Want, AbilityConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class MyAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    this.context.setMissionContinueState(AbilityConstant.ContinueState.INACTIVE, (result: BusinessError) => {
      console.info(`setMissionContinueState: ${JSON.stringify(result)}`);
    });
  }
}
```

## CollaborateResult<sup>18+</sup>

Enumerates the collaboration request results. You can use it in multi-device collaboration scenarios to specify whether the target application accepts the collaboration request from the caller application. You can use it in [onCollaborate()](js-apis-app-ability-uiAbility.md#oncollaborate18) of the UIAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name    | Value  | Description      |
| -------- | ---- | ---------- |
| ACCEPT   | 0    | Accepts the collaboration request.|
| REJECT   | 1    | Rejects the collaboration request.|

**Example**

```ts
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

export default class MyAbility extends UIAbility {
  onCollaborate(wantParam: Record<string, Object>) {
    return AbilityConstant.CollaborateResult.ACCEPT;
  }
}
```

## PrepareTermination<sup>15+</sup>

Enumerates the actions triggered when an application is closed by the user. You can use it in [onPrepareTermination](js-apis-app-ability-abilityStage.md#onpreparetermination15) or [onPrepareTerminationAsync](js-apis-app-ability-abilityStage.md#onprepareterminationasync15) of [AbilityStage](js-apis-app-ability-abilityStage.md).

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Value| Description|
| ------------- | --------- | ----------- |
| TERMINATE_IMMEDIATELY | 0 | Immediately performs the termination action. |
| CANCEL | 1 | Cancels the termination action.|

**Example**

```ts
import { AbilityConstant, AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onPrepareTermination(): AbilityConstant.PrepareTermination {
    console.info('MyAbilityStage.onPrepareTermination is called');
    return AbilityConstant.PrepareTermination.CANCEL;
  }
}
```