# ApplicationStateObserver
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=54a85e57a9e078c186b756489db16f65a538d313 translatedAt=2026-09-03T11:42:49.863Z pushedAt=2026-09-05T10:47:30.677Z -->

The module defines an observer to listen for application state changes. It can be used as an input parameter in [on('applicationState')](js-apis-app-ability-appManager.md#appmanageronapplicationstate14) to listen for lifecycle changes of the application.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## ApplicationStateObserver.onForegroundApplicationChanged

onForegroundApplicationChanged(appStateData: AppStateData): void

Called when the foreground or background state of an application changes.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| appStateData | [AppStateData](js-apis-inner-application-appStateData.md) | Yes| Application state data.|

## ApplicationStateObserver.onAbilityStateChanged

onAbilityStateChanged(abilityStateData: AbilityStateData): void

Called when the [Ability](js-apis-app-ability-ability.md) state changes.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| abilityStateData | [AbilityStateData](js-apis-inner-application-abilityStateData.md) | Yes| Ability state data.|

## ApplicationStateObserver.onProcessCreated

onProcessCreated(processData: ProcessData): void

Called when a process is created.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| processData | [ProcessData](js-apis-inner-application-processData.md) | Yes| Process data.|

## ApplicationStateObserver.onProcessDied

onProcessDied(processData: ProcessData): void

Called when a process is destroyed.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| processData | [ProcessData](js-apis-inner-application-processData.md) | Yes| Process data.|

## ApplicationStateObserver.onProcessStateChanged

onProcessStateChanged(processData: ProcessData): void

Called when the process state changes.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| processData | [ProcessData](js-apis-inner-application-processData.md) | Yes| Process data.|

## ApplicationStateObserver.onAppStarted

onAppStarted(appStateData: AppStateData): void

Called when the first process of the application is created.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| appStateData | [AppStateData](js-apis-inner-application-appStateData.md) | Yes| Application state data.|

## ApplicationStateObserver.onAppStopped

onAppStopped(appStateData: AppStateData): void

Called when the last process of the application is destroyed.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| appStateData | [AppStateData](js-apis-inner-application-appStateData.md) | Yes| Application state data.|

## ProcessData

type ProcessData = _ProcessData.default

Defines the process data.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| _[ProcessData](js-apis-inner-application-processData.md).default | Process data information. |

**Example**
```ts
import { appManager } from '@kit.AbilityKit';

let applicationStateObserver: appManager.ApplicationStateObserver = {
  onForegroundApplicationChanged(appStateData) {
    console.info(`onForegroundApplicationChanged, appStateData: ${JSON.stringify(appStateData)}.`);
  },
  onAbilityStateChanged(abilityStateData) {
    console.info(`onAbilityStateChanged, abilityStateData: ${JSON.stringify(abilityStateData)}.`);
  },
  onProcessCreated(processData) {
    console.info(`onProcessCreated, processData: ${JSON.stringify(processData)}.`);
  },
  onProcessDied(processData) {
    console.info(`onProcessDied, processData: ${JSON.stringify(processData)}.`);
  },
  onProcessStateChanged(processData) {
    console.info(`onProcessStateChanged, processData: ${JSON.stringify(processData)}.`);
  },
  onAppStarted(appStateData) {
    console.info(`onAppStarted, appStateData: ${JSON.stringify(appStateData)}.`);
  },
  onAppStopped(appStateData) {
    console.info(`onAppStopped, appStateData: ${JSON.stringify(appStateData)}.`);
  }
};
let observerCode = appManager.on('applicationState', applicationStateObserver);
```