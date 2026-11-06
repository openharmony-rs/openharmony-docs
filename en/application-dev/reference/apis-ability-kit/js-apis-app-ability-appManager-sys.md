# @ohos.app.ability.appManager (appManager) (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7fe4eacae9c952d492316e40f501d71d3714186d translatedAt=2026-09-03T09:59:45.767Z pushedAt=2026-09-05T10:47:30.241Z -->

The appManager module provides application management capabilities, including querying whether the application is undergoing a stability test, whether the device is RAM-constrained, obtaining the memory size of an application, and obtaining information about running processes.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This page contains only the system APIs of this module. For details about other public APIs, see [@ohos.app.ability.appManager (Application Management)](js-apis-app-ability-appManager.md).

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## appManager.PreloadMode<sup>12+</sup>

Enumerates the modes used for preloading an application process.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name       | Value | Description                        |
| ----------- | --- | --------------------------- |
| PRESS_DOWN  | 0 | The application process is preloaded when the application icon is pressed.|

## KeepAliveAppType<sup>14+</sup>

Enumerates the types of applications to be kept alive.

**System API**: This is a system API.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

| Name       | Value | Description|
| -------- | ---------- | -------- |
| ALL  | 0 | Third-party and system applications. This value can be called only as an input parameter of [getKeepAliveBundles](#appmanagergetkeepalivebundles14). |
| THIRD_PARTY | 1  | Third-party application. |
| SYSTEM | 2 | System application.|

## KeepAliveSetter<sup>14+</sup>

Enumerates the types of parties that set to keep applications alive.

**System API**: This is a system API.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

| Name       | Value | Description|
| -------- | ---------- | -------- |
| SYSTEM | 0 | System, which means that the system sets to keep applications alive.|
| USER  | 1 | User, which means that a user sets to keep applications alive. |

## KeepAliveBundleInfo<sup>14+</sup>

Describes the keep-alive application information, which can be obtained by calling [getKeepAliveBundles](#appmanagergetkeepalivebundles14) or [getKeepAliveAppServiceExtensions](#appmanagergetkeepaliveappserviceextensions20).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

| Name| Type| Read-Only| Optional | Description|
| ------------------------- | ------ | ---- | ---- | --------- |
| bundleName   | string | No| No | Bundle name.|
| type       | [KeepAliveAppType](#keepaliveapptype14) | No| No| Type of the application to be kept alive.  |
| setter       | [KeepAliveSetter](#keepalivesetter14) | No | No | Type of the application keep-alive setter.   |
| setterUserId<sup>20+</sup>   | number | No | Yes  | User ID of the application keep-alive setter. |
| allowUserToCancel<sup>20+</sup>   | boolean | No| Yes | Whether the user can cancel the keep-alive status. **true** if yes, **false** otherwise.|

## appManager.isSharedBundleRunning<sup>10+</sup>

isSharedBundleRunning(bundleName: string, versionCode: number): Promise\<boolean>

Checks whether the shared library is in use. This API uses a promise to return the result.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name       | Type                                      | Mandatory  | Description            |
| --------- | ---------------------------------------- | ---- | -------------- |
| bundleName    | string   | Yes   | Bundle name of the shared library.|
| versionCode   | number   | Yes   | Version number of the shared library.     |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<boolean> | Promise object. The value true indicates that the shared library is in use, and the value false indicates that the shared library is not in use. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const bundleName = 'com.example.myapplication';
const versionCode = 1;

appManager.isSharedBundleRunning(bundleName, versionCode).then((data) => {
  console.info(`The shared bundle running is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```

## appManager.isSharedBundleRunning<sup>10+</sup>

isSharedBundleRunning(bundleName: string, versionCode: number, callback: AsyncCallback\<boolean>): void

Checks whether the shared library is in use. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name       | Type                                      | Mandatory  | Description            |
| --------- | ---------------------------------------- | ---- | -------------- |
| bundleName    | string   | Yes   | Bundle name of the shared library.|
| versionCode   | number   | Yes   | Version number of the shared library.     |
| callback    | AsyncCallback\<boolean> | Yes    | Callback function. Returns true if the shared library is in use, and false otherwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';

const bundleName = 'com.example.myapplication';
const versionCode = 1;

appManager.isSharedBundleRunning(bundleName, versionCode, (err, data) => {
  if (err) {
    console.error(`err: ${JSON.stringify(err)}`);
  } else {
    console.info(`The shared bundle running is: ${JSON.stringify(data)}`);
  }
});
```

## appManager.on('appForegroundState')<sup>11+</sup>

on(type: 'appForegroundState', observer: AppForegroundStateObserver): void

Registers a listener for application startup, foreground and background, and exit. It can be used by system applications to listen for the startup, foreground and background, and exit of all applications.

**System API**: This is a system API.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'appForegroundState'**.|
| observer | [AppForegroundStateObserver](js-apis-inner-application-appForegroundStateObserver-sys.md) | Yes | Application state observer used to listen for the startup, foreground and background, and exit of an application. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
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

## appManager.on('abilityFirstFrameState')<sup>12+</sup>

on(type: 'abilityFirstFrameState', observer: AbilityFirstFrameStateObserver, bundleName?: string): void

Registers an observer to listen for the complete of the first frame rendering of a given ability.

**System API**: This is a system API.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                                        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type       | string                                                       | Yes  | Event type. It is fixed at **'abilityFirstFrameState'**.        |
| observer   | [AbilityFirstFrameStateObserver](js-apis-inner-application-abilityFirstFrameStateObserver-sys.md#abilityfirstframestateobserver) | Yes   | Observer object for the Ability first frame rendering completion event to be registered.              |
| bundleName | string                                                       | No  | Bundle name of the ability to be listened for. If this parameter is left blank, the event is listened for all applications.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
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

## appManager.off('appForegroundState')<sup>11+</sup>

off(type: 'appForegroundState', observer?: AppForegroundStateObserver): void

Unregisters the listener for application startup, foreground and background, and exit.

**System API**: This is a system API.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Event type. It is fixed at **'appForegroundState'**.|
| observer | [AppForegroundStateObserver](js-apis-inner-application-appForegroundStateObserver-sys.md) | No | Application startup, foreground and background, and exit observer to unregister. If this parameter is left empty, all observed objects are unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let savedObserver: appManager.AppForegroundStateObserver | undefined;
// 1. Register an observer to listen for application start or exit events.
let observer: appManager.AppForegroundStateObserver = {
  onAppStateChanged(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStateChanged: ${JSON.stringify(appStateData)}`);
  },
};

try {
  appManager.on('appForegroundState', observer);
  // Save the observer object.
  savedObserver = observer;
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

// 2. Deregister the observer.
try {
  appManager.off('appForegroundState',  savedObserver);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.off('abilityFirstFrameState')<sup>12+</sup>

off(type: 'abilityFirstFrameState', observer?: AbilityFirstFrameStateObserver): void

Deregisters the observer used to listen for the complete of the first frame rendering of a given ability.

**System API**: This is a system API.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. It is fixed at **'abilityFirstFrameState'**.        |
| observer | [AbilityFirstFrameStateObserver](js-apis-inner-application-abilityFirstFrameStateObserver-sys.md#abilityfirstframestateobserver) | No | Observer object of the Ability first frame rendering completion event to be unsubscribed. If this parameter is left empty, all observed objects are unsubscribed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
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

try {
  appManager.off('abilityFirstFrameState', abilityFirstFrameStateObserverForAll);
} catch (e) {
  let code = (e as BusinessError).code;
  let message = (e as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.on('applicationState')<sup>21+</sup>

on(type: 'applicationState', observer: ApplicationStateObserver, filter: AppStateFilter): number

Registers an application state observer, which allows you to filter for specific application lifecycle changes by setting filter criteria.

**System API**: This is a system API.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the API to call. It is fixed at **'applicationState'**.|
| observer | [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) | Yes| Application state observer, which is used to listen for application lifecycle changes.|
| filter | [AppStateFilter](#appstatefilter21) | Yes| Filter for application lifecycle changes.|

**Return value**

| Type| Description|
| --- | --- |
| number | ID of the observer registered. You can pass this ID to [off](js-apis-app-ability-appManager.md#appmanageroffapplicationstate14) to unregister the observer.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module.|

**Example**

```ts
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

## appManager.getForegroundApplications

getForegroundApplications(callback: AsyncCallback\<Array\<AppStateData>>): void

Obtains applications that are running in the foreground. The application information is defined by [AppStateData](js-apis-inner-application-appStateData.md). This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback\<Array\<[AppStateData](js-apis-inner-application-appStateData.md)>> | Yes| Callback used to return the API call result and an array holding the application state data. You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function getForegroundApplicationsCallback(err: BusinessError, data: Array<appManager.AppStateData>) {
  if (err) {
    console.error(`getForegroundApplicationsCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info(`getForegroundApplicationsCallback success, data: ${JSON.stringify(data)}`);
  }
}

try {
  appManager.getForegroundApplications(getForegroundApplicationsCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.getForegroundApplications

getForegroundApplications(): Promise\<Array\<AppStateData>>

Obtains applications that are running in the foreground. The application information is defined by [AppStateData](js-apis-inner-application-appStateData.md). This API uses a promise to return the result.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<[AppStateData](js-apis-inner-application-appStateData.md)>> | Promise used to return an array holding the application state data.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.getForegroundApplications().then((data) => {
  console.info(`getForegroundApplications success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getForegroundApplications fail, err: ${JSON.stringify(err)}`);
});
```

## appManager.killProcessWithAccount

killProcessWithAccount(bundleName: string, accountId: number): Promise\<void\>

Kills the application process under the specified system account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is not required when **accountId** specifies the current user.

**Required permissions:**

- API versions 9 to 13: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES
- API version 14 and later: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES, or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| accountId | number | Yes| ID of a system account. For details, see [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9).|

**Return value**

| Type            | Description             |
| -------------- | --------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let accountId = 0;

try {
  appManager.killProcessWithAccount(bundleName, accountId).then(() => {
    console.info('killProcessWithAccount success');
  }).catch((err: BusinessError) => {
    console.error(`killProcessWithAccount fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.killProcessWithAccount<sup>14+</sup>

killProcessWithAccount(bundleName: string, accountId: number, clearPageStack: boolean, appIndex?: number): Promise\<void\>

Kills the application process under the specified system account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is not required when **accountId** specifies the current user.

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES, or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| accountId | number | Yes| ID of a system account. For details, see [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9).|
| clearPageStack | boolean | Yes| Whether to clear the page stack. **true** to clear, **false** otherwise.|
| appIndex | number | No | Application clone ID. The value must be an integer greater than or equal to 0, and the default value **0** indicates the main application. Pass this parameter when the process of a specified clone application needs to be terminated. If this parameter is not passed, the main application is processed by default. |

**Return value**

| Type            | Description             |
| -------------- | --------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let accountId = 0;
let isClearPageStack = false;
let appIndex = 1;

try {
  appManager.killProcessWithAccount(bundleName, accountId, isClearPageStack, appIndex).then(() => {
    console.info('killProcessWithAccount success');
  }).catch((err: BusinessError) => {
    console.error(`killProcessWithAccount fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.killProcessWithAccount

killProcessWithAccount(bundleName: string, accountId: number, callback: AsyncCallback\<void\>): void

Terminates the application process under a specified system account. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is not required when **accountId** specifies the current user.

**Required Permission:**

- API version 9 to 13: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES
- API version 14 or later: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES, or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | bundleName | string | Yes| Bundle name.|
  | accountId | number | Yes| ID of a system account. For details, see [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9).|
  | callback | AsyncCallback\<void\> | Yes| Callback used to return the API call result. You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let accountId = 0;

function killProcessWithAccountCallback(err: BusinessError) {
  if (err) {
    console.error(`killProcessWithAccountCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('killProcessWithAccountCallback success.');
  }
}

appManager.killProcessWithAccount(bundleName, accountId, killProcessWithAccountCallback);
```

## appManager.killProcessesByBundleName

killProcessesByBundleName(bundleName: string, callback: AsyncCallback\<void>): void

Terminates the process of the main application by bundle name. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API does not support terminating the process of an application clone.

**Required Permission:**

- API version 9 to 13: ohos.permission.CLEAN_BACKGROUND_PROCESSES
- API version 14 or later: ohos.permission.KILL_APP_PROCESSES or ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| callback | AsyncCallback\<void> | Yes| Callback used to return the API call result. You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';

function killProcessesByBundleNameCallback(err: BusinessError) {
  if (err) {
    console.error(`killProcessesByBundleNameCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('killProcessesByBundleNameCallback success.');
  }
}

try {
  appManager.killProcessesByBundleName(bundleName, killProcessesByBundleNameCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.killProcessesByBundleName

killProcessesByBundleName(bundleName: string): Promise\<void>

Terminates the process of the main application by bundle name. This API uses a promise to return the result.

> **NOTE**
>
> This API does not support terminating the process of a clone application.

**Required Permission:**

- API version 9 to 13: ohos.permission.CLEAN_BACKGROUND_PROCESSES
- API version 14 or later: ohos.permission.KILL_APP_PROCESSES or ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';

try {
  appManager.killProcessesByBundleName(bundleName).then((data) => {
    console.info('killProcessesByBundleName success.');
  }).catch((err: BusinessError) => {
    console.error(`killProcessesByBundleName fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.clearUpApplicationData

clearUpApplicationData(bundleName: string, callback: AsyncCallback\<void>): void

Clears application data by bundle name. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.CLEAN_APPLICATION_DATA

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| callback | AsyncCallback\<void> | Yes| Callback used to return the API call result. You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';

function clearUpApplicationDataCallback(err: BusinessError) {
  if (err) {
    console.error(`clearUpApplicationDataCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('clearUpApplicationDataCallback success.');
  }
}

try {
  appManager.clearUpApplicationData(bundleName, clearUpApplicationDataCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.clearUpApplicationData

clearUpApplicationData(bundleName: string): Promise\<void>

Clears application data by bundle name. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CLEAN_APPLICATION_DATA

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise object. A Promise object that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';

try {
  appManager.clearUpApplicationData(bundleName).then((data) => {
    console.info('clearUpApplicationData success.');
  }).catch((err: BusinessError) => {
    console.error(`clearUpApplicationData fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.getProcessMemoryByPid<sup>10+</sup>

getProcessMemoryByPid(pid: number, callback: AsyncCallback\<number>): void

Obtains the memory size of a process. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| pid | number | Yes | Process ID. For details, see [getRunningProcessInfoByBundleName](#appmanagergetrunningprocessinfobybundlename10). |
| callback | AsyncCallback\<number> | Yes| Callback used to return the API call result and the memory size (in KB). You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let pid = 0;
function getProcessMemoryByPidCallback(err: BusinessError, data: number) {
  if (err) {
    console.error(`getProcessMemoryByPidCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('getProcessMemoryByPidCallback success.');
  }
}

try {
  appManager.getProcessMemoryByPid(pid, getProcessMemoryByPidCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.getProcessMemoryByPid<sup>10+</sup>

getProcessMemoryByPid(pid: number): Promise\<number>

Obtains the memory size of a process. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| pid | number | Yes | Process ID. For details, see [getRunningProcessInfoByBundleName](#appmanagergetrunningprocessinfobybundlename10). |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<number> | Promise used to return the API call result and the memory size (in KB). You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let pid = 0;

try {
  appManager.getProcessMemoryByPid(pid).then((data) => {
    console.info('getProcessMemoryByPid success.');
  }).catch((err: BusinessError) => {
    console.error(`getProcessMemoryByPid fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.getRunningProcessInfoByBundleName<sup>10+</sup>

getRunningProcessInfoByBundleName(bundleName: string, callback: AsyncCallback\<Array\<ProcessInformation>>): void

Obtains the running process information of the main application and clone applications of the current user by bundle name. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| callback | AsyncCallback\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Yes| Callback used to return the API call result and the process running information. You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
function getRunningProcessInfoByBundleNameCallback(err: BusinessError, data: Array<appManager.ProcessInformation>) {
  if (err) {
    console.error(`getRunningProcessInfoByBundleNameCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('getRunningProcessInfoByBundleNameCallback success.');
  }
}

try {
  appManager.getRunningProcessInfoByBundleName(bundleName, getRunningProcessInfoByBundleNameCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.getRunningProcessInfoByBundleName<sup>10+</sup>

getRunningProcessInfoByBundleName(bundleName: string): Promise\<Array\<ProcessInformation>>

Obtains the running process information of the main application and clone applications of the current user by bundle name. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Promise used to return the API call result and the process running information. You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';

try {
  appManager.getRunningProcessInfoByBundleName(bundleName).then((data) => {
    console.info('getRunningProcessInfoByBundleName success.');
  }).catch((err: BusinessError) => {
    console.error(`getRunningProcessInfoByBundleName fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.getRunningProcessInfoByBundleName<sup>10+</sup>

getRunningProcessInfoByBundleName(bundleName: string, userId: number, callback: AsyncCallback\<Array\<ProcessInformation>>): void

Obtains the running process information of the corresponding main application and clone applications by bundle name and user ID. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| userId | number | Yes | User ID. |
| callback | AsyncCallback\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Yes| Callback used to return the API call result and the process running information. You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let userId = 0;
function getRunningProcessInfoByBundleNameCallback(err: BusinessError, data: Array<appManager.ProcessInformation>) {
  if (err) {
    console.error(`getRunningProcessInfoByBundleNameCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('getRunningProcessInfoByBundleNameCallback success.');
  }
}

try {
  appManager.getRunningProcessInfoByBundleName(bundleName, userId, getRunningProcessInfoByBundleNameCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.getRunningProcessInfoByBundleName<sup>10+</sup>

getRunningProcessInfoByBundleName(bundleName: string, userId: number): Promise\<Array\<ProcessInformation>>

Obtains the running process information of the corresponding main application and clone applications by bundle name and user ID. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| userId | number | Yes | User ID. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Promise used to return the API call result and the process running information. You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 202 | Permission denied, non-system app called system api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let userId = 0;

try {
  appManager.getRunningProcessInfoByBundleName(bundleName, userId).then((data) => {
    console.info('getRunningProcessInfoByBundleName success.');
  }).catch((err: BusinessError) => {
    console.error(`getRunningProcessInfoByBundleName fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.isApplicationRunning<sup>11+</sup>

isApplicationRunning(bundleName: string): Promise\<boolean>

Checks whether the main application with the specified bundle name is running under all users. This API uses a promise to return the result.

> **NOTE**
>
> This API does not support querying whether an application clone is running.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name       | Type                                      | Mandatory  | Description            |
| --------- | ---------------------------------------- | ---- | -------------- |
| bundleName    | string   | Yes   | Bundle name.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<boolean> | Promise used to return the result. **true** is returned if at least one user is running the specified application. **false** is returned if none of the users are running the application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';

appManager.isApplicationRunning(bundleName).then((data) => {
  console.info(`The application running is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```

## appManager.isApplicationRunning<sup>11+</sup>

isApplicationRunning(bundleName: string, callback: AsyncCallback\<boolean>): void

Checks whether the main application with the specified bundle name is running for all users. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API does not support querying whether an application clone is running.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name       | Type                                      | Mandatory  | Description            |
| --------- | ---------------------------------------- | ---- | -------------- |
| bundleName    | string   | Yes   | Bundle name.|
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. **true** is returned if at least one user is running the specified application. **false** is returned if none of the users are running the application.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';

try {
  appManager.isApplicationRunning(bundleName, (err, data) => {
    if (err) {
      console.error(`err: ${JSON.stringify(err)}`);
    } else {
      console.info(`The application running is: ${JSON.stringify(data)}`);
    }
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## ApplicationState

Enumerates the application states. This enum can be used together with [AbilityStateData](js-apis-inner-application-abilityStateData.md) to return the application state.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

| Name                | Value | Description                              |
| -------------------- | --- | --------------------------------- |
| STATE_CREATE    | 0   |   The application is being created.        |
| STATE_FOREGROUND          | 2   |      The application is running in the foreground.           |
| STATE_ACTIVE  | 3   |     The application is active.    |
| STATE_BACKGROUND        | 4   |    The application is running in the background.          |
| STATE_DESTROY        | 5   |    The application is being destroyed.      |


## appManager.getRunningProcessInformationByBundleType<sup>12+</sup>

getRunningProcessInformationByBundleType(bundleType: bundleManager.BundleType): Promise\<Array\<ProcessInformation>>

Obtains information about the current running processes by bundle type. This information can be used for classified management of running processes or resource monitoring. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name       | Type                                      | Mandatory  | Description            |
| --------- | ---------------------------------------- | ---- | -------------- |
| bundleType    | [bundleManager.BundleType](js-apis-bundleManager.md#bundletype)  | Yes   | Bundle type.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Promise used to return the process information.|

**Error codes**
For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |


**Example**

```ts
import { appManager, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appManager.getRunningProcessInformationByBundleType(bundleManager.BundleType.ATOMIC_SERVICE)
    .then((data) => {
      console.info(`The running process information is: ${JSON.stringify(data)}`);
    }).catch((error: BusinessError) => {
    console.error(`error: ${JSON.stringify(error)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.preloadApplication<sup>12+</sup>

preloadApplication(bundleName: string, userId: number, mode: PreloadMode, appIndex?: number): Promise\<void>

Preloads an application process. A successful call does not always mean that the preloading is successful. In other words, the target application process may not be created even if the API is successfully called. This API uses a promise to return the result.

> **NOTE**
>
> This API does not support preloading an application clone. The **appIndex** parameter can only be set to **0**. Passing any other value returns error code 16000050.

**Required permissions**: ohos.permission.PRELOAD_APPLICATION

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name of the application to preload.|
| userId | number | Yes | ID of the user to preload. |
| mode | [PreloadMode](#appmanagerpreloadmode12) | Yes| Mode used for preloading.|
| appIndex | number | No | appIndex of the preloaded application clone. This parameter can only be set to 0. Preloading application clones is not supported currently. |

**Return value**

| Type          | Description             |
| -------------- | ---------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

  For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | The application does not have permission to call the interface. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |
| 16300005 | The target bundle does not exist. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let bundleName = 'ohos.samples.etsclock';
  let userId = 100;
  let mode = appManager.PreloadMode.PRESS_DOWN;
  let appIndex = 0;
  appManager.preloadApplication(bundleName, userId, mode, appIndex)
    .then(() => {
      hilog.info(0x0000, 'testTag', `preloadApplication success`);
    })
    .catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `preloadApplication error, code: ${err.code}, msg:${err.message}`);
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', `preloadApplication error, code: ${(err as BusinessError).code}, msg:${(err as BusinessError).message}`);
}
```

## appManager.getRunningMultiAppInfo<sup>12+</sup>

getRunningMultiAppInfo(bundleName: string): Promise\<RunningMultiAppInfo>

Obtains information about the running application clones (multiple instances of the same application running on one device) by bundle name. This information can be used for multi-instance management or resource allocation. This API uses a promise to return the result.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|

**Return value**

| Type          | Description             |
| -------------- | ---------------- |
| Promise\<[RunningMultiAppInfo](js-apis-inner-application-runningMultiAppInfo-sys.md)> | Promise used to return the information about running applications with multi-app mode.|

**Error codes**

  For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000072 | App clone or multi-instance is not supported. |
| 18500001 | The bundle does not exist or no patch has been applied. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.etsclock';
  appManager.getRunningMultiAppInfo(bundleName).then((info: appManager.RunningMultiAppInfo) => {
      hilog.info(0x0000, 'testTag', `getRunningMultiAppInfo success`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `getRunningMultiAppInfo error, code: ${err.code}, msg:${err.message}`);
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', `getRunningMultiAppInfo error, code: ${(err as BusinessError).code}, msg:${(err as BusinessError).message}`);
}
```

## appManager.terminateMission<sup>13+</sup>

terminateMission(missionId: number): Promise\<void>

Terminates a mission. This API uses a promise to return the result.

**Required permissions**: ohos.permission.KILL_APP_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| missionId | number | Yes| Mission ID, which can be obtained by calling [getMissionInfos](js-apis-app-ability-missionManager-sys.md#missionmanagergetmissioninfos).|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**
```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Button('start link', { type: ButtonType.Capsule, stateEffect: true })
      .width('87%')
      .height('5%')
      .margin({ bottom: '12vp' })
      .onClick(() => {
        let missionId: number = 0;
        try {
          appManager.terminateMission(missionId).then(()=>{
              console.info('terminateMission success.');
            }).catch((err: BusinessError)=>{
              console.error('terminateMission failed. err: ' + JSON.stringify(err));
            })
        } catch (paramError) {
          let code = (paramError as BusinessError).code;
          let message = (paramError as BusinessError).message;
          console.error(`[appManager] error: ${code}, ${message}`);
        }
      })
  }
}
```

## appManager.getSupportedProcessCachePids<sup>14+</sup>

getSupportedProcessCachePids(bundleName: string): Promise\<Array\<number>>

Obtains the PIDs of processes that support quick startup after caching in the current application. This information can be used for process management. This API uses a promise to return the result.

> **NOTE**
>
> This API can only be used to obtain the PIDs of the system account to which the caller belongs.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName    | string   | Yes   | Bundle name.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<number>> | Promise used to return an array containing the PIDs.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.processcache';
  appManager.getSupportedProcessCachePids(bundleName).then((pids: Array<number>) => {
      hilog.info(0x0000, 'testTag', `pids: ${JSON.stringify(pids)}`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `get pids error, code: ${err.code}, msg:${err.message}`);
    })
} catch (err) {
  hilog.error(0x0000, 'testTag', `get pids error, code: ${(err as BusinessError).code}, msg:${(err as BusinessError).message}`);
}
```

## appManager.clearUpAppData<sup>13+</sup>

clearUpAppData(bundleName: string, appCloneIndex?: number): Promise\<void>

Clears data of a specified application based on the bundle name and application clone index. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CLEAN_APPLICATION_DATA

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| appCloneIndex | number | No | Application clone index. Pass this parameter when you need to clear the data of a specified clone application. If this parameter is not passed, the data of the main application is cleared by default (appCloneIndex is 0). |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |
| 16000073 | The app clone index is invalid. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = 'com.ohos.demo';
let appCloneIndex: number = 0;

try {
  appManager.clearUpAppData(bundleName, appCloneIndex).then(() => {
    console.info(`clearUpAppData success.`);
  }).catch((err: BusinessError) => {
    console.error(`clearUpAppData fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.setKeepAliveForBundle<sup>14+</sup>

setKeepAliveForBundle(bundleName: string, userId: number, enable: boolean): Promise\<void>

Sets or cancels the keep-alive status for an application that belongs to a specified user. This API uses a promise to return the result.

> **NOTE**
>
>- To support keep-alive, the **mainElement** in the [module.json5 configuration file](../../quick-start/module-configuration-file.md) of the application must be a UIAbility. The system performs the application keep-alive operation only after the mainElement is started.
>- On PC/2-in-1 devices, a keep-alive application must be added to the status bar within 5 seconds after startup. Otherwise, the system cancels the keep-alive setting of the application and kills the process restarted for keep-alive.
>- When the process of a keep-alive application exits, the system attempts to restart the process. After three consecutive restart failures, the system stops restarting it.
>- This API does not support setting or canceling the keep-alive state of an application clone (specified user and bundle name).

**Permission required**: ohos.permission.MANAGE_APP_KEEP_ALIVE

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior difference**: Since API version 18, this API takes effect only on PC/2-in-1 and wearable devices. For versions earlier than API version 18, this API takes effect only on PC/2-in-1 devices. In other cases, calling this API returns error code 801.

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName    | string   | Yes   | Bundle name.|
| userId    | number   | Yes   | User ID.|
| enable    | boolean   | Yes   | Whether to keep the application alive or cancel its keep-alive status. **true** to keep the application alive, **false** otherwise.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. |
| 16000050 | Internal error. |
| 16300005 | The target bundle does not exist. |
| 16300008 | The target bundle has no MainAbility. |
| 16300009 | The target bundle has no status-bar ability. |
| 16300010 | The target application is not attached to the status bar. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.keepaliveapp';
  let userId = 100;
  appManager.setKeepAliveForBundle(bundleName, userId, true).then(() => {
    console.info(`setKeepAliveForBundle success`);
  }).catch((err: BusinessError) => {
    console.error(`setKeepAliveForBundle fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] setKeepAliveForBundle error: ${code}, ${message}`);
}
```

## appManager.getKeepAliveBundles<sup>14+</sup>

getKeepAliveBundles(type: KeepAliveAppType, userId?: number): Promise\<Array\<KeepAliveBundleInfo>>

Obtains the keep-alive application information of the specified type for the specified user. This API can be used for keep-alive application management or resource monitoring. The application information is defined by [KeepAliveBundleInfo](#keepalivebundleinfo14). This API uses a promise to return the result.

**Permission required**: ohos.permission.MANAGE_APP_KEEP_ALIVE

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned.

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type    | [KeepAliveAppType](#keepaliveapptype14)   | Yes   | Type of the application.|
| userId    | number   | No    | User ID of the keep-alive application to query. Pass this parameter when you need to query the keep-alive applications of a specific user. If this parameter is not passed, the keep-alive applications of the current user are queried by default. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<[KeepAliveBundleInfo](#keepalivebundleinfo14)>> | Promise used to return the array of keep-alive application information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userId = 100;
let type: appManager.KeepAliveAppType = appManager.KeepAliveAppType.THIRD_PARTY;
try {
  appManager.getKeepAliveBundles(type, userId).then((data) => {
    console.info(`getKeepAliveBundles success, data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`getKeepAliveBundles fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] getKeepAliveBundles error: ${code}, ${message}`);
}
```


## appManager.killProcessesInBatch<sup>14+</sup>

killProcessesInBatch(pids: Array\<number>): Promise\<void>

Kills processes in batches. This API uses a promise to return the result.

**Required permissions**: ohos.permission.KILL_APP_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned.

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| pids    | Array\<number>   | Yes   | Array of process IDs.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let pids: Array<number> = [100, 101, 102];
  appManager.killProcessesInBatch(pids).then(() => {
    console.info(`killProcessesInBatch success`);
  }).catch((err: BusinessError) => {
    console.error(`killProcessesInBatch fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] killProcessesInBatch error: ${code}, ${message}`);
}
```

## appManager.setKeepAliveForAppServiceExtension<sup>20+</sup>

setKeepAliveForAppServiceExtension(bundleName: string, enabled: boolean): Promise\<void>

Sets or cancels the keep-alive status for an AppServiceExtensionAbility. This API uses a promise to return the result.
> **NOTE**
>
> - This API takes effect only when the application is installed under the user with **userId** of 1 and the **mainElement** field in the **module.json5** file of the entry HAP is set to **AppServiceExtensionAbility**.

**Permission required**: ohos.permission.MANAGE_APP_KEEP_ALIVE

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned.

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName    | string   | Yes   | Bundle name.|
| enabled    | boolean   | Yes   | Whether to keep the application alive or cancel its keep-alive status. **true** to keep, **false** otherwise.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 801 | Capability not supported. |
| 16000050 | Internal error. |
| 16000081 | Failed to obtain the target application information. |
| 16000202 | Invalid main element type. |
| 16000203 | Cannot change the keep-alive status. |
| 16000204 | The target bundle is not in u1. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.keepaliveapp';
  appManager.setKeepAliveForAppServiceExtension(bundleName, true).then(() => {
    console.info(`setKeepAliveForAppServiceExtension success`);
  }).catch((err: BusinessError) => {
    console.error(`setKeepAliveForAppServiceExtension fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] setKeepAliveForAppServiceExtension error: ${code}, ${message}`);
}
```

## appManager.getKeepAliveAppServiceExtensions<sup>20+</sup>

getKeepAliveAppServiceExtensions(): Promise\<Array\<KeepAliveBundleInfo>>

Obtains the information about all keep-alive AppServiceExtensionAbility applications. The information is defined by [KeepAliveBundleInfo](#keepalivebundleinfo14) and can be used for service management or resource monitoring. This API uses a promise to return the result.

**Permission required**: ohos.permission.MANAGE_APP_KEEP_ALIVE

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned.

**System API**: This is a system API.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<[KeepAliveBundleInfo](#keepalivebundleinfo14)>> | Promise used to return the array of keep-alive application information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 202 | Not system application. |
| 801 | Capability not supported. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  appManager.getKeepAliveAppServiceExtensions().then((data) => {
    console.info(`getKeepAliveAppServiceExtensions success, data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`getKeepAliveAppServiceExtensions fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] getKeepAliveAppServiceExtensions error: ${code}, ${message}`);
}
```

## appManager.getProcessRunningInfos<sup>(deprecated)</sup>

getProcessRunningInfos(): Promise\<Array\<ProcessInformation>>

Obtains information about running processes. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [appManager.getRunningProcessInformation](js-apis-app-ability-appManager.md#appmanagergetrunningprocessinformation) instead.

**Required Permission**: ohos.permission.GET_RUNNING_INFO (available only to system applications)

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Promise object used to return the information about running processes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  appManager.getProcessRunningInfos().then((data) => {
    console.info(`The process running infos is: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`error: ${JSON.stringify(error)}`);
  });
  ```

## appManager.getProcessRunningInfos<sup>(deprecated)</sup>

getProcessRunningInfos(callback: AsyncCallback\<Array\<ProcessInformation>>): void

Obtains information about running processes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [appManager.getRunningProcessInformation](js-apis-app-ability-appManager.md#appmanagergetrunningprocessinformation) instead.

**Required Permission:** ohos.permission.GET_RUNNING_INFO (available only to system applications)

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Yes | Callback invoked to return the information about running processes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. Possible causes: 1. Failed to connect to the system service; 2. The system service failed to communicate with dependency module. |

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';

  appManager.getProcessRunningInfos((error, data) => {
    if (error && error.code !== 0) {
      console.error(`getProcessRunningInfos fail, error: ${JSON.stringify(error)}`);
    } else {
      console.info(`getProcessRunningInfos success, data: ${JSON.stringify(data)}`);
    }
  });
  ```

## AppForegroundStateObserver<sup>11+</sup>

type AppForegroundStateObserver = _AppForegroundStateObserver.default

Observes the application startup, foreground and background, and exit states.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AppForegroundStateObserver](js-apis-inner-application-appForegroundStateObserver-sys.md).default | Observes the application startup, foreground and background, and exit states. |

## AbilityFirstFrameStateObserver<sup>12+</sup>

type AbilityFirstFrameStateObserver = _AbilityFirstFrameStateObserver.default

Defines the listener for the completion of the first frame rendering of the UIAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [AbilityFirstFrameStateObserver](js-apis-inner-application-abilityFirstFrameStateObserver-sys.md#abilityfirstframestateobserver).default | Observed object for the UIAbility first frame rendering completion event. |

## AbilityFirstFrameStateData<sup>12+</sup>

type AbilityFirstFrameStateData = _AbilityFirstFrameStateData.default

Defines the data structure reported when the first frame rendering of the UIAbility is complete.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityFirstFrameStateData](js-apis-inner-application-abilityFirstFrameStateData-sys.md).default | Data structure reported by the callback when the first frame rendering of the UIAbility is complete. |

## RunningMultiAppInfo<sup>12+</sup>

type RunningMultiAppInfo = _RunningMultiAppInfo

Defines the information of an application in multi-app mode in the running state.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_RunningMultiAppInfo](js-apis-inner-application-runningMultiAppInfo-sys.md) | Information of the application in multi-app mode in the running state.|

## FilterBundleType<sup>21+</sup>

Represents the application types to observe. This is an enum. It can be used with [AppStateFilter](#appstatefilter21) to filter the application types to observe.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name       | Value | Description|
| -------- | ---------- | -------- |
| APP | 1 << 0 | Application. |
| ATOMIC_SERVICE | 1 << 1 | Atomic service. |

## FilterAppStateType<sup>21+</sup>

Enumerates the types of application states to filter. It can be used with [AppStateFilter](#appstatefilter21) to filter the application state types you want to listen for.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name       | Value | Description|
| -------- | ---------- | -------- |
| CREATE | 1 << 0 | The application is being initialized, corresponding to the state where the value of **state** in the [properties](js-apis-inner-application-appStateData.md#properties) of AppStateData is 0. |
| FOREGROUND | 1 << 1 | The application is in the foreground, corresponding to the state where the value of **state** in the [properties](js-apis-inner-application-appStateData.md#properties) of AppStateData is 2. |
| BACKGROUND | 1 << 2 | The application is in the background, corresponding to the state where the value of **state** in the [properties](js-apis-inner-application-appStateData.md#properties) of AppStateData is 4. |
| DESTROY | 1 << 3 | The application has exited, corresponding to the state where the value of **state** in the [properties](js-apis-inner-application-appStateData.md#properties) of AppStateData is 5. |

## FilterProcessStateType<sup>21+</sup>

Enumerates the types of process states to filter. It can be used with [AppStateFilter](#appstatefilter21) to filter the process state types you want to listen for.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name       | Value | Description|
| -------- | ---------- | -------- |
| CREATE | 1 << 0 | The process has just been created, corresponding to the state where the value of state in ProcessData [properties](js-apis-inner-application-processData.md#properties) is 0. |
| FOREGROUND | 1 << 1 | The process is in the foreground, corresponding to the state where the value of state in ProcessData [properties](js-apis-inner-application-processData.md#properties) is 2. |
| BACKGROUND | 1 << 2 | The process is in the background, corresponding to the state where the value of state in ProcessData [properties](js-apis-inner-application-processData.md#properties) is 4. |
| DESTROY | 1 << 3 | The process has been terminated, corresponding to the state where the value of state in ProcessData [properties](js-apis-inner-application-processData.md#properties) is 5. |

## FilterAbilityStateType<sup>21+</sup>

Enumerates the types of ability states to filter. It can be used with [AppStateFilter](#appstatefilter21) to filter the ability state types you want to listen for.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name       | Value | Description|
| -------- | ---------- | -------- |
| CREATE | 1 << 0 | The ability is being created, corresponding to the state with the value **0** in [UIAbility state](js-apis-inner-application-abilityStateData.md#uiability-states), [ExtensionAbility state](js-apis-inner-application-abilityStateData.md#extensionability-states), and [UIExtensionAbility state](js-apis-inner-application-abilityStateData.md#uiextensionability-states). |
| FOREGROUND | 1 << 1 | The ability is in the foreground, corresponding to the state with the value **2** in [UIAbility state](js-apis-inner-application-abilityStateData.md#uiability-states) and [UIExtensionAbility state](js-apis-inner-application-abilityStateData.md#uiextensionability-states). |
| BACKGROUND | 1 << 2 | The ability is in the background, corresponding to the state with the value **4** in [UIAbility state](js-apis-inner-application-abilityStateData.md#uiability-states) and [UIExtensionAbility state](js-apis-inner-application-abilityStateData.md#uiextensionability-states). |
| DESTROY | 1 << 3 | The ability has been destroyed, corresponding to the state with the value **5** in [UIAbility state](js-apis-inner-application-abilityStateData.md#uiability-states), [ExtensionAbility state](js-apis-inner-application-abilityStateData.md#extensionability-states), and [UIExtensionAbility state](js-apis-inner-application-abilityStateData.md#uiextensionability-states), and the state with the value **4** in [ExtensionAbility state](js-apis-inner-application-abilityStateData.md#extensionability-states). |

## FilterCallback<sup>21+</sup>

Enumerates the callbacks to filter. It can be used with [AppStateFilter](#appstatefilter21) to filter the callbacks you want to listen for.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name       | Value | Description|
| -------- | ---------- | -------- |
| ON_FOREGROUND_APPLICATION_CHANGED | 1 << 0 | Callback invoked when the foreground and background state of an application changes, corresponding to [ApplicationStateObserver.onForegroundApplicationChanged](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronforegroundapplicationchanged). |
| ON_ABILITY_STATE_CHANGED | 1 << 1 | Callback invoked when the ability state changes, corresponding to [ApplicationStateObserver.onAbilityStateChanged](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronabilitystatechanged). |
| ON_PROCESS_CREATED | 1 << 2 | Callback invoked when a process is created, corresponding to [ApplicationStateObserver.onProcessCreated](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocesscreated). |
| ON_PROCESS_DIED | 1 << 3 | Callback invoked when a process is destroyed, corresponding to [ApplicationStateObserver.onProcessDied](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocessdied). |
| ON_PROCESS_STATE_CHANGED | 1 << 4 | Callback invoked when the process state is updated, corresponding to [ApplicationStateObserver.onProcessStateChanged](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocessstatechanged). |
| ON_APP_STARTED | 1 << 5 | Callback invoked when the first process of an application is created, corresponding to [ApplicationStateObserver.onAppStarted](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronappstarted). |
| ON_APP_STOPPED | 1 << 6 | Callback invoked when the last process of an application is destroyed, corresponding to [ApplicationStateObserver.onAppStopped](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronappstopped). |

## AppStateFilter<sup>21+</sup>

Describes the filter for application lifecycle change events. It can be used as a parameter of [on](#appmanageronapplicationstate21) to filter application lifecycle change events you want to listen for.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

| Name| Type| Read-Only| Optional | Description|
| ------------------------- | ------ | ---- | ---- | --------- |
| bundleTypes  | number | No  | Yes  | Application type to observe. The value range is as follows:<br> - 0: no application type is observed.<br> - A bitwise OR combination of the enums in [FilterBundleType](#filterbundletype21): for example, "appManager.FilterBundleType.APP \| appManager.FilterBundleType.ATOMIC_SERVICE" indicates that the lifecycle change events of both common applications and atomic services are observed.<br> - If this parameter is not set, all application types are observed by default.|
| appStateTypes | number | No | Yes | Application state to observe. The value range is as follows:<br> - 0: no application state is observed.<br> - A bitwise OR combination of the enums in [FilterAppStateType](#filterappstatetype21): for example, "appManager.FilterAppStateType.CREATE \| appManager.FilterAppStateType.FOREGROUND" indicates that both the created state and the foreground state of applications are observed.<br> - If this parameter is not set, all application states are observed by default.|
| processStateTypes | number | No | Yes | Process state to observe. The value range is as follows:<br> - 0: no process state is observed.<br> - A bitwise OR combination of the enums in [FilterProcessStateType](#filterprocessstatetype21): for example, "appManager.FilterProcessStateType.CREATE \| appManager.FilterProcessStateType.FOREGROUND" indicates that both the created state and the foreground state of processes are observed.<br> - If this parameter is not set, all process states are observed by default.|
| abilityStateTypes | number | No | Yes  | Ability state to observe. The value range is as follows:<br> - 0: no Ability state is observed.<br> - A bitwise OR combination of the enums in [FilterAbilityStateType](#filterabilitystatetype21): for example, "appManager.FilterAbilityStateType.CREATE \| appManager.FilterAbilityStateType.FOREGROUND" indicates that both the created state and the foreground state of abilities are observed.<br> - If this parameter is not set, all Ability states are observed by default.|
| callbacks | number | No | Yes  | Callback function to observe. The value range is as follows:<br> - 0: no callback function is observed.<br> - A bitwise OR combination of the enums in [FilterCallback](#filtercallback21): for example, "appManager.FilterCallback.ON_ABILITY_STATE_CHANGED \| appManager.FilterCallback.ON_PROCESS_STATE_CHANGED" indicates that both [ApplicationStateObserver.onAbilityStateChanged](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronabilitystatechanged) and [ApplicationStateObserver.onProcessStateChanged](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronprocessstatechanged) are observed.<br> - If this parameter is not set, all callback functions corresponding to [FilterCallback](#filtercallback21) are observed by default.|