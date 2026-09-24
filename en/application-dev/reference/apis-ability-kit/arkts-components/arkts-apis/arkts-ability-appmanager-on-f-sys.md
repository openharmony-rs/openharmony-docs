# on (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## on('applicationState')

```TypeScript
function on(type: 'applicationState', observer: ApplicationStateObserver, filter: AppStateFilter): number
```

Registers an application state observer, which allows you to filter for specific application lifecycle changes by setting filter criteria.

**Since:** 21

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'applicationState' | Yes | Type of the API to call. It is fixed at **'applicationState'**. |
| observer | [ApplicationStateObserver](arkts-ability-appmanager-applicationstateobserver-t.md) | Yes | Application state observer, which is used to listen for application lifecycle changes. |
| filter | [AppStateFilter](arkts-ability-appmanager-appstatefilter-i-sys.md) | Yes | Filter for application lifecycle changes. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the observer registered. You can pass this ID to off to unregister the observer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let applicationStateObserver: appManager.ApplicationStateObserver = {
  onForegroundApplicationChanged(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onForegroundApplicationChanged: ${JSON.stringify(appStateData)}`);
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

/* This example uses the filter to listen for the following application callbacks:
 * 1. onAbilityStateChanged, a callback function used to listen for ability components in the creating state.
 * 2. onProcessCreated, a callback function used to listen for processes in the created state.
 */
let appStateFilter: appManager.AppStateFilter = {
    bundleTypes: appManager.FilterBundleType.APP,
    appStateTypes: appManager.FilterAppStateType.CREATE | appManager.FilterAppStateType.FOREGROUND,
    processStateTypes: appManager.FilterProcessStateType.CREATE,
    abilityStateTypes: appManager.FilterAbilityStateType.CREATE,
    callbacks: appManager.FilterCallback.ON_ABILITY_STATE_CHANGED | appManager.FilterCallback.ON_PROCESS_CREATED
};

try {
  const observerId = appManager.on('applicationState', applicationStateObserver, appStateFilter);
  console.info(`[appManager] observerCode: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```


## on('appForegroundState')

```TypeScript
function on(type: 'appForegroundState', observer: AppForegroundStateObserver): void
```

Registers an observer to listen for application start or exit events. The observer can be used by a system application to observe the start or event events of all applications.

**Since:** 11

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'appForegroundState' | Yes | Event type. It is fixed at **'appForegroundState'**. |
| observer | [AppForegroundStateObserver](arkts-ability-appmanager-appforegroundstateobserver-t-sys.md) | Yes | Observer used to listen for application start or exit events. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: appManager.AppForegroundStateObserver = {
  onAppStateChanged(appStateData) {
    console.info(`[appManager] onAppStateChanged: ${JSON.stringify(appStateData)}`);
  },
};

try {
  appManager.on('appForegroundState', observer);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```


## on('abilityFirstFrameState')

```TypeScript
function on(type: 'abilityFirstFrameState', observer: AbilityFirstFrameStateObserver, bundleName?: string): void
```

Registers an observer to listen for the complete of the first frame rendering of a given ability.

**Since:** 12

**Required permissions:** ohos.permission.RUNNING_STATE_OBSERVER

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'abilityFirstFrameState' | Yes | Event type. It is fixed at **'abilityFirstFrameState'**. |
| observer | [AbilityFirstFrameStateObserver](arkts-ability-appmanager-abilityfirstframestateobserver-t-sys.md) | Yes | Observer used to listen for the complete of the first frame rendering of the ability. |
| bundleName | string | No | Bundle name of the ability to be listened for. If this parameter is left blank, the event is listened for all applications. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityFirstFrameStateObserverForAll: appManager.AbilityFirstFrameStateObserver = {
  onAbilityFirstFrameDrawn(abilityStateData: appManager.AbilityFirstFrameStateData) {
    console.info('abilityFirstFrame: ', JSON.stringify(abilityStateData));
  }
};

try {
  appManager.on('abilityFirstFrameState', abilityFirstFrameStateObserverForAll);
} catch (e) {
  let code = (e as BusinessError).code;
  let message = (e as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```
