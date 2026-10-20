# ProcessData

```TypeScript
declare class ProcessData
```

The module defines process data. If a lifecycle change listener is registered by calling [appManager.on('applicationState')](arkts-ability-appmanager-on-f.md#onapplicationstate), the [onProcessCreated](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocesscreated) callback in [ApplicationStateObserver](arkts-ability-applicationstateobserver-c.md) is invoked when the lifecycle of an application or ability changes.

**Since:** 14

<!--Device-unnamed-declare class ProcessData--><!--Device-unnamed-declare class ProcessData-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 14

<!--Device-ProcessData-bundleName: string--><!--Device-ProcessData-bundleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isContinuousTask

```TypeScript
isContinuousTask: boolean
```

Whether the task is a continuous task. **true** if yes, **false** otherwise.

**Type:** boolean

**Since:** 14

<!--Device-ProcessData-isContinuousTask: boolean--><!--Device-ProcessData-isContinuousTask: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isKeepAlive

```TypeScript
isKeepAlive: boolean
```

Whether the process is a resident task. **true** if yes, **false** otherwise.

**Type:** boolean

**Since:** 14

<!--Device-ProcessData-isKeepAlive: boolean--><!--Device-ProcessData-isKeepAlive: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## pid

```TypeScript
pid: number
```

Process ID.

**Type:** number

**Since:** 14

<!--Device-ProcessData-pid: int--><!--Device-ProcessData-pid: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: number
```

Application state. The options are as follows:

**0**: The application process is being initialized.

**1**: The application process has been initialized and is ready.

**2**: The application is running in the foreground.

**4**: The application is running in the background.

**5**: The application process is terminated.

**Type:** number

**Since:** 14

<!--Device-ProcessData-state: int--><!--Device-ProcessData-state: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Since:** 14

<!--Device-ProcessData-uid: int--><!--Device-ProcessData-uid: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';

let observerCode = appManager.on('applicationState', {
  onForegroundApplicationChanged(appStateData: appManager.AppStateData) {
    console.info(`onForegroundApplicationChanged, appStateData: ${JSON.stringify(appStateData)}.`);
  },
  onAbilityStateChanged(abilityStateData: appManager.AbilityStateData) {
    console.info(`onAbilityStateChanged, abilityStateData: ${JSON.stringify(abilityStateData)}.`);
  },
  onProcessCreated(processData: appManager.ProcessData) {
    console.info(`onProcessCreated, processData: ${JSON.stringify(processData)}.`);
  },
  onProcessDied(processData: appManager.ProcessData) {
    console.info(`onProcessDied, processData: ${JSON.stringify(processData)}.`);
  },
  onProcessStateChanged(processData: appManager.ProcessData) {
    console.info(`onProcessStateChanged, processData.pid : ${JSON.stringify(processData.pid)}.`);
    console.info(`onProcessStateChanged, processData.bundleName : ${JSON.stringify(processData.bundleName)}.`);
    console.info(`onProcessStateChanged, processData.uid : ${JSON.stringify(processData.uid)}.`);
    console.info(`onProcessStateChanged, processData.isContinuousTask : ${JSON.stringify(processData.isContinuousTask)}.`);
    console.info(`onProcessStateChanged, processData.isKeepAlive : ${JSON.stringify(processData.isKeepAlive)}.`);
  },
  onAppStarted(appStateData: appManager.AppStateData) {
    console.info(`onAppStarted, appStateData: ${JSON.stringify(appStateData)}.`);
  },
  onAppStopped(appStateData: appManager.AppStateData) {
    console.info(`onAppStopped, appStateData: ${JSON.stringify(appStateData)}.`);
  }
});
```
