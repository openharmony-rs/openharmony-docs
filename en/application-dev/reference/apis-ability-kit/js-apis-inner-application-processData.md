# ProcessData
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=83eb20b2da17b66d3089c14abb21986b856a3985 translatedAt=2026-09-03T12:02:10.326Z pushedAt=2026-09-05T10:47:30.856Z -->

Defines the process data object. After the lifecycle change listener is registered using [appManager.on('applicationState')](js-apis-app-ability-appManager.md#appmanageronapplicationstate14), when the lifecycle of an application or component changes, the system reports ProcessData to the developer through methods such as [onProcessCreated](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocesscreated) of [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md).

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
| isKeepAlive      | boolean   | No   | No | Whether the process is a resident process. The value **true** means the process is a resident process, and **false** means the opposite.                   |
| state       | number   | No   |  No | State of the process. The value can be:<br>0 - Initial state. The process is being initialized.<br>1 - Ready state. The process has been initialized.<br>2 - Foreground.<br>4 - Background.<br>5 - Terminated.     |

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
