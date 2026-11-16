# @ohos.app.ability.AppProcessStateObserver (Application Process State Observer)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=efa9eed0898124a6dea71f057e0a7afdff1f3f9a translatedAt=2026-11-14T08:07:08.759Z pushedAt=2026-11-14T08:13:00.014Z nl=1 -->

Defines an application process state observer, which is used to listen for the creation and termination of in-app processes. Developers can call [ApplicationContext.onAppProcessStateChange](js-apis-inner-application-applicationContext.md) to pass in a custom AppProcessStateObserver to listen for in-app process state changes and perform corresponding operations. For example, initialize resources when a process is created and clean up resources when a process is terminated.

**Since:** 26.1.0

> **NOTE**
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { AppProcessStateObserver } from '@kit.AbilityKit';
```

## AppProcessStateObserver.onProcessCreated

onProcessCreated(processData: ProcessData): void

Called when an in-app process is created.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| processData | [ProcessData](js-apis-inner-application-processData.md) | Yes | Process data, including the process ID, bundle name, application UID, and process state. |

**Example**

See [onProcessDied](#appprocessstateobserveronprocessdied).

## AppProcessStateObserver.onProcessDied

onProcessDied(processData: ProcessData): void

Called when an in-app process is destroyed.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| processData | [ProcessData](js-apis-inner-application-processData.md) | Yes | Process data, including the process ID, bundle name, application UID, process state, and other information. |

**Example**

```ts
import { UIAbility, AppProcessStateObserver, appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appProcessStateObserver: AppProcessStateObserver = {
  onProcessCreated(processData: appManager.ProcessData) {
    console.info(`onProcessCreated, processData: ${JSON.stringify(processData)}`);
  },
  onProcessDied(processData: appManager.ProcessData) {
    console.info(`onProcessDied, processData: ${JSON.stringify(processData)}`);
  }
};

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      // Register the listener for in-app process state changes.
      applicationContext.onAppProcessStateChange(appProcessStateObserver);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info('Register appProcessStateObserver');
  }

  // Unregister the listener when it is no longer needed or when the application exits.
  onDestroy() {
    // Obtain the application context.
    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.offAppProcessStateChange(appProcessStateObserver);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```
