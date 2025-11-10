# ProcessData
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The module defines process data. If a lifecycle change listener is registered by calling [appManager.on('applicationState')](js-apis-app-ability-appManager.md#appmanageronapplicationstate14), the [onProcessCreated](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocesscreated) callback in [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) is invoked when the lifecycle of an application or ability changes.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## Properties

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name        | Type    | Read-Only| Optional| Description                      |
| ------------| ---------| ---- | ---- | ------------------------- |
| pid         | number   | No  | No| Process ID.                   |
| bundleName  | string   | No  | No| Bundle name of the application.                 |
| uid         | number   | No  | No|UID of the application.                 |
| isContinuousTask | boolean   | No  | No| Whether the task is a continuous task. **true** if yes, **false** otherwise.                |
| isKeepAlive      | boolean   | No  | No|Whether the process is a resident task. **true** if yes, **false** otherwise.                  |
| state       | number   | No  |  No|Application state. The options are as follows:<br>**0**: The application process is being initialized.<br>**1**: The application process has been initialized and is ready.<br>**2**: The application is running in the foreground.<br>**4**: The application is running in the background.<br>**5**: The application process is terminated.    |

**Example**
```ts
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
