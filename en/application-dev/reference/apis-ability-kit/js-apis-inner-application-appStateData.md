# AppStateData
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=8e4ee7947dfeb3a89be0dfff4e576f69a510a94f translatedAt=2026-09-03T11:43:34.574Z pushedAt=2026-09-05T10:47:30.680Z -->

The module defines the application state information. Once an application state change listener is registered using [on](js-apis-app-ability-appManager.md#appmanageronapplicationstate14), the system triggers the [onForegroundApplicationChanged](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronforegroundapplicationchanged) callback of [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) to deliver notifications whenever the state of an application, process, or ability changes.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 14. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## Properties

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                     | Type  | Read-Only | Optional | Description      |
| ------------------------- | ------ | ---- | ---- | ---------- |
| bundleName  | string | No  | No  | Bundle name.|
| uid          | number | No  | No  | UID of the application.  |
| state        | number | No  | No  | Application state.<br>0: initializing state, the application is being initialized;<br>1: ready state, the application has been initialized;<br>2: foreground state, the application is in the foreground;<br>3: focused state (reserved, not supported yet);<br>4: background state, the application is in the background;<br>5: exited state, the application has exited. |
| isSplitScreenMode | boolean | No | No | Whether the application is in split-screen mode.<br>true: the application is in split-screen mode.<br>false: the application is not in split-screen mode. |
| isFloatingWindowMode | boolean | No | No | Whether the application is in floating window mode.<br>true: the application is in floating window mode.<br>false: the application is not in floating window mode. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let applicationStateObserver: appManager.ApplicationStateObserver = {
  onForegroundApplicationChanged(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
    console.info(`appStateData.bundleName: ${appStateData.bundleName}`);
    console.info(`appStateData.uid: ${appStateData.uid}`);
    console.info(`appStateData.state: ${appStateData.state}`);
    console.info(`appStateData.isSplitScreenMode: ${appStateData.isSplitScreenMode}`);
    console.info(`appStateData.isFloatingWindowMode: ${appStateData.isFloatingWindowMode}`);
  },
  onAbilityStateChanged(abilityStateData: appManager.AbilityStateData) {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  },
  onProcessCreated(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  },
  onProcessDied(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  },
  onProcessStateChanged(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  },
  onAppStarted(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  },
  onAppStopped(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
};

try {
  const observerId = appManager.on('applicationState', applicationStateObserver);
  console.info(`[appManager] observerId: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error code: ${code}, error msg: ${message}`);
}
```
