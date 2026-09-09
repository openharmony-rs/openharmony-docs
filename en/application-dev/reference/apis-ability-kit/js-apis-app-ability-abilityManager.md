# @ohos.app.ability.abilityManager (Ability Information Management)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @dsz2025 -->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=9b45198dbdb6f53f8bf0896d62425626f2442690 translatedAt=2026-09-03T09:52:38.038Z pushedAt=2026-09-05T10:47:30.211Z -->

The AbilityManager module provides ability information management, including obtaining the ability running status, restarting atomic services, and determining device capability support.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version. 

## Modules to Import

```ts
import { abilityManager } from '@kit.AbilityKit';
```

## AbilityState<sup>14+</sup>

Enumerates the ability states. This enum can be used together with [AbilityRunningInfo](js-apis-inner-application-abilityRunningInfo.md) to return the ability state.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Value| Description|
| -------- | -------- | -------- |
| INITIAL | 0 | Indicates that the ability is in the initial state. |
| FOCUS | 2 | Indicates that the ability is in the focused state. |
| FOREGROUND | 9 | Indicates that the ability is in the foreground state. |
| BACKGROUND | 10 | Indicates that the ability is in the background state. |
| FOREGROUNDING | 11 | Indicates that the ability is in the foregrounding state. |
| BACKGROUNDING | 12 | Indicates that the ability is in the backgrounding state. |


## abilityManager.getAbilityRunningInfos<sup>14+</sup>

getAbilityRunningInfos(): Promise\<Array\<AbilityRunningInfo>>

Obtains the running information of UIAbility, including the process ID, ability name, and status. This API uses a promise to return the result.

> **NOTE**
>
> If the application has requested the ohos.permission.GET_RUNNING_INFO permission, it can obtain the UIAbility running information of all applications; otherwise, it can obtain the UIAbility running information of the current application.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| Promise\<Array\<[AbilityRunningInfo](js-apis-inner-application-abilityRunningInfo.md)>> | Promise object used to return the runtime information of the UIAbility. Developers can handle errors or customize the processing of the returned data here. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000050 | Internal error. |

**Example**

```ts
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Obtain UIAbility runtime information.
  abilityManager.getAbilityRunningInfos()
    .then((data: abilityManager.AbilityRunningInfo[]) => {
      console.info(`getAbilityRunningInfos success, data: ${JSON.stringify(data)}`);
    })
    .catch((error: BusinessError) => {
      console.error(`getAbilityRunningInfos fail, error code: ${JSON.stringify(error.code)}, error msg: ${JSON.stringify(error.message)}`);
    })
} catch (e) {
  let code = (e as BusinessError).code;
  let msg = (e as BusinessError).message;
  console.error(`getAbilityRunningInfos fail, error code: ${JSON.stringify(code)}, error msg: ${JSON.stringify(msg)}`);
}
```

## abilityManager.restartSelfAtomicService<sup>20+</sup>

restartSelfAtomicService(context: Context): void

Restarts the current atomic service.

> **NOTE**
>
> - Currently, atomic services can be started only in an independent window.
>
> - If you call this API, [ApplicationContext.restartApp()](js-apis-inner-application-applicationContext.md#applicationcontextrestartapp12), or [UIAbilityContext.restartApp()](js-apis-inner-application-uiAbilityContext.md#restartapp22) within 3 seconds after a successful call to this API, the system returns error code 16000064.


**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Parameters**

| Name       | Type                                      | Mandatory  | Description            |
| --------- | ---------------------------------------- | ---- | -------------- |
| context    | [Context](./js-apis-inner-application-context.md)   | Yes    | Context of the current ability, used to provide the execution environment information required for restarting the atomic service.<br>**Note:** Currently, only [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md) is supported. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module.|
| 16000053 | The ability is not on the top of the UI. |
| 16000064 | Restart too frequently. Try again at least 3s later. |
| 16000086 | The context is not UIAbilityContext. |
| 16000090 | The caller is not an atomic service. |

**Example**

```ts
import { AbilityConstant, EmbeddableUIAbility, Want, abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends EmbeddableUIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Restart the current atomic service.
      abilityManager.restartSelfAtomicService(this.context);
    } catch (e) {
      console.error(`restartSelfAtomicService error: ${JSON.stringify(e as BusinessError)}`);
    }
  }
}
```

## abilityManager.isEmbeddedUIExtensionSupported

isEmbeddedUIExtensionSupported(): boolean

Checks whether [EmbeddedUIExtensionAbility](../../application-models/embeddeduiextensionability.md) can be used on the current device.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type | Description |
| -------- | -------- |
| boolean | Whether the current device supports [EmbeddedUIExtensionAbility](../../application-models/embeddeduiextensionability.md). The value **true** indicates that the current device supports it, and **false** indicates the opposite. |

**Example**

```ts
import { abilityManager, UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    // Determine whether the current device supports EmbeddedUIExtensionAbility.
    let isSupported: boolean = abilityManager.isEmbeddedUIExtensionSupported();
    console.info(`isEmbeddedUIExtensionSupported is ${isSupported}`);
  }
}
```

## AbilityRunningInfo<sup>14+</sup>

type AbilityRunningInfo = _AbilityRunningInfo

Defines the level-2 module AbilityRunningInfo.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityRunningInfo](js-apis-inner-application-abilityRunningInfo.md) | AbilityRunningInfo, a level-2 module that provides the information and state related to an ability.|

## AbilityStateData<sup>14+</sup>

type AbilityStateData = _AbilityStateData.default

Defines the level-2 module AbilityStateData.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityStateData](js-apis-inner-application-abilityStateData.md).default | Second-level module of AbilityStateData, which provides Ability state information. |
