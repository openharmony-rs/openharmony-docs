# AppStateData

```TypeScript
declare class AppStateData
```

The module defines the application state information. Once an application state change listener is registered using [on](arkts-ability-appmanager-on-f.md#onapplicationstate), the system triggers the [onForegroundApplicationChanged](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronforegroundapplicationchanged) callback of [ApplicationStateObserver](arkts-ability-applicationstateobserver-c.md) to deliver notifications whenever the state of an application, process, or ability changes.

**Since:** 14

<!--Device-unnamed-declare class AppStateData--><!--Device-unnamed-declare class AppStateData-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Since:** 14

<!--Device-AppStateData-bundleName: string--><!--Device-AppStateData-bundleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isFloatingWindowMode

```TypeScript
isFloatingWindowMode: boolean
```

Whether the application is in floating window mode.

**true**: The application is in floating window mode.

**false**: The application is not in floating window mode.

**Type:** boolean

**Since:** 14

<!--Device-AppStateData-isFloatingWindowMode: boolean--><!--Device-AppStateData-isFloatingWindowMode: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## isSplitScreenMode

```TypeScript
isSplitScreenMode: boolean
```

Whether the application is in split-screen mode.

**true**: The application is in split-screen mode.

**false**: The application is not in split-screen mode.

**Type:** boolean

**Since:** 14

<!--Device-AppStateData-isSplitScreenMode: boolean--><!--Device-AppStateData-isSplitScreenMode: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: number
```

Application state.

**0**: The application is being initialized.

**1**: The application has been initialized and is ready.

**2**: The application is running in the foreground.

**3**: The application is having the focus. (This state is reserved.)

**4**: The application is running in the background.

**5**: The application has exited.

**Type:** number

**Since:** 14

<!--Device-AppStateData-state: int--><!--Device-AppStateData-state: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Since:** 14

<!--Device-AppStateData-uid: int--><!--Device-AppStateData-uid: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
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
