# @ohos.app.ability.appManager (Application Management)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=fd4a15396b80efc1154943b82adce302d07cd529 translatedAt=2026-09-03T09:58:12.209Z pushedAt=2026-09-05T10:47:30.233Z -->

The appManager module provides APIs for application management. For example, you can query whether the system is undergoing a stability test, determine whether the device is RAM-constrained, obtain the maximum memory available to the current application, and retrieve information about running processes.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## ProcessState<sup>10+</sup>

Enumerates the processes states.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                | Value | Description                              |
| -------------------- | --- | --------------------------------- |
| STATE_CREATE    | 0   |    The process is created.      |
| STATE_FOREGROUND          | 1   |    The process is running in the foreground.     |
| STATE_ACTIVE  | 2   |     At least one window in the process has focus.  |
| STATE_BACKGROUND        | 3   |    The process is running in the background.          |
| STATE_DESTROY        | 4   |    The process is destroyed.        |

## appManager.isRunningInStabilityTest

isRunningInStabilityTest(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the system is undergoing a stability test. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> A stability test scenario refers to a specific testing environment designed to verify application reliability under complex, extreme, or long-term operating conditions.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the API call is successful, **err** is **undefined** and **data** is the check result for whether the system is undergoing a stability test. Otherwise, **err** is an error object. You can perform error handling or other custom processing.<br>**true** is returned if the system is undergoing a stability test; **false** is returned otherwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';

appManager.isRunningInStabilityTest((err, flag) => {
  if (err) {
    console.error(`isRunningInStabilityTest fail, code: ${err.code}, msg:${err.message}`);
  } else {
    console.info(`The result of isRunningInStabilityTest is: ${JSON.stringify(flag)}`);
  }
});
```


## appManager.isRunningInStabilityTest

isRunningInStabilityTest(): Promise&lt;boolean&gt;

Checks whether the system is undergoing a stability test. This API uses a promise to return the result.

> **NOTE**
>
> A stability test scenario refers to a specific testing environment designed to verify application reliability under complex, extreme, or long-term operating conditions.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise object. Returns true if the system is in a stability test scenario; returns false otherwise. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.isRunningInStabilityTest().then((flag) => {
  console.info(`The result of isRunningInStabilityTest is: ${JSON.stringify(flag)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```


## appManager.isRamConstrainedDevice

isRamConstrainedDevice(): Promise\<boolean>

Checks whether the current device is a RAM-constrained device (a device with severely limited memory resources). This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise object. The value true indicates that the current device is a RAM-restricted device; the value false indicates that the current device is not a RAM-restricted device. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.isRamConstrainedDevice().then((data) => {
  console.info(`The result of isRamConstrainedDevice is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```

## appManager.isRamConstrainedDevice

isRamConstrainedDevice(callback: AsyncCallback\<boolean>): void

Checks whether the current device is a RAM-constrained device (a device with severely limited memory resources). This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the API call is successful, **err** is **undefined** and **data** is the check result for whether the device is RAM-constrained. Otherwise, **err** is an error object. You can perform error handling or other custom processing.<br>**true** is returned if the device is RAM-constrained; **false** is returned otherwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';

appManager.isRamConstrainedDevice((err, data) => {
  if (err) {
    console.error(`isRamConstrainedDevice fail, code: ${err.code}, msg:${err.message}`);
  } else {
    console.info(`The result of isRamConstrainedDevice is: ${JSON.stringify(data)}`);
  }
});
```

## appManager.getAppMemorySize

getAppMemorySize(): Promise\<number>

Obtains the maximum memory (RAM allocation) available to the current application. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Promise&lt;number&gt; | Promise object that returns the maximum memory (RAM) value available to the current application. This value can be used for error handling or other custom processing, in MB. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.getAppMemorySize().then((data) => {
  console.info(`The size of app memory is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`code: ${error.code}, msg:${error.message}`);
});
```

## appManager.getAppMemorySize

getAppMemorySize(callback: AsyncCallback\<number>): void

Obtains the maximum memory (RAM allocation) available to the current application. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;number&gt; | Yes | Callback function. If the API call is successful, err is undefined and data is the maximum memory (RAM) available to the current application, in MB. Otherwise, err is an error object. You can perform error handling or other custom processing based on this value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';

appManager.getAppMemorySize((err, data) => {
  if (err) {
    console.error(`getAppMemorySize fail, code: ${err.code}, msg:${err.message}`);
  } else {
    console.info(`The size of app memory is: ${JSON.stringify(data)}`);
  }
});
```

## appManager.getRunningProcessInformation

getRunningProcessInformation(): Promise\<Array\<ProcessInformation>>

Starting from API version 11, only the process information of the caller is returned by default. If the caller has the ohos.permission.GET_RUNNING_INFO permission (available only for system applications), the process information of all applications can be queried. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Required permissions:**

API versions 9 to 10: ohos.permission.GET_RUNNING_INFO (available only for system applications)

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Promise used to return the API call result and the process running information. You can perform error handling or custom processing in this callback.|

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.getRunningProcessInformation().then((data) => {
  console.info(`The running process information is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`code: ${error.code}, msg:${error.message}`);
});
```

## appManager.getRunningProcessInformation

getRunningProcessInformation(callback: AsyncCallback\<Array\<ProcessInformation>>): void

Starting from API version 11, only the process information of the caller is returned by default. If the caller has the ohos.permission.GET_RUNNING_INFO permission (available only for system applications), the process information of all applications can be queried. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Required permissions:**

API versions 9 to 10: ohos.permission.GET_RUNNING_INFO (available only for system applications)

**Parameters**

  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback\<Array\<[ProcessInformation](js-apis-inner-application-processInformation.md)>> | Yes| Callback used to return the result. If the API call is successful, **err** is **undefined** and **data** is the information about the running processes. Otherwise, **err** is an error object. You can perform error handling or other custom processing.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';

appManager.getRunningProcessInformation((err, data) => {
  if (err) {
    console.error(`getRunningProcessInformation fail, code: ${err.code}, msg:${err.message}`);
  } else {
    console.info(`The running process information is: ${JSON.stringify(data)}`);
  }
});
```

## appManager.on('applicationState')<sup>14+</sup>

on(type: 'applicationState', observer: ApplicationStateObserver): number

Registers an observer to listen for lifecycle changes of all applications.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the API to call. It is fixed at **'applicationState'**.|
| observer | [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) | Yes| Application state observer, which is used to listen for applications lifecycle changes.|

**Return value**

| Type| Description|
| --- | --- |
| number | ID of the observer registered. You can pass this ID to [off('applicationState')](#appmanageroffapplicationstate14) to unregister the observer.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

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

try {
  const observerId = appManager.on('applicationState', applicationStateObserver);
  console.info(`[appManager] observerCode: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.on('applicationState')<sup>14+</sup>

on(type: 'applicationState', observer: ApplicationStateObserver, bundleNameList: Array\<string>): number

Registers an observer to listen for lifecycle changes of the specified application.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the API to call. It is fixed at **'applicationState'**.|
| observer | [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) | Yes| Application state observer, which is used to listen for application lifecycle changes.|
| bundleNameList | `Array<string>` | Yes | Array of bundle names for which listeners need to be registered. The maximum number is 128. If this number is exceeded, error code 16000050 is returned. |

**Return value**

| Type| Description|
| --- | --- |
| number | ID of the observer registered. You can pass this ID to [off('applicationState')](#appmanageroffapplicationstate14) to unregister the observer.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

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

let bundleNameList = ['bundleName1', 'bundleName2'];

try {
  const observerId = appManager.on('applicationState', applicationStateObserver, bundleNameList);
  console.info(`[appManager] observerCode: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.off('applicationState')<sup>14+</sup>

off(type: 'applicationState', observerId: number): Promise\<void>

Unregisters the observer used to listen for application state changes. This API uses a promise to return the result.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the API to call. It is fixed at **'applicationState'**.|
| observerId | number | Yes| ID of the observer registered, which is the listener ID returned by [on('applicationState')](#appmanageronapplicationstate14).|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 0;

// 1. Register an application state observer.
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
let bundleNameList = ['bundleName1', 'bundleName2'];

try {
  observerId = appManager.on('applicationState', applicationStateObserver, bundleNameList);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

// 2. Unregister the application state observer.
try {
  appManager.off('applicationState', observerId).then((data) => {
    console.info(`unregisterApplicationStateObserver success, data: ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`unregisterApplicationStateObserver fail, code: ${err.code}, msg:${err.message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.off('applicationState')<sup>15+</sup>

off(type: 'applicationState', observerId: number, callback: AsyncCallback\<void>): void

Unregisters the observer used to listen for application state changes. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the API to call. It is fixed at **'applicationState'**.|
| observerId | number | Yes| ID of the observer registered, which is the listener ID returned by [on('applicationState')](#appmanageronapplicationstate14).|
| callback | AsyncCallback\<void> | Yes | Callback function. When the application state listener is unregistered successfully, err is undefined; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observerId = 0;

// 1. Register an application state observer.
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
let bundleNameList = ['bundleName1', 'bundleName2'];

try {
  observerId = appManager.on('applicationState', applicationStateObserver, bundleNameList);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}

function offCallback(err: BusinessError) {
  if (err) {
    console.error(`appmanager.off failed, code: ${err.code}, msg: ${err.message}`);
  } else {
    console.info(`appmanager.off success.`);
  }
}

// 2. Unregister the application state observer.
try {
  appManager.off('applicationState', observerId, offCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.killProcessesByBundleName<sup>14+</sup>

killProcessesByBundleName(bundleName: string, clearPageStack: boolean, appIndex?: number): Promise\<void>

Kills a process by bundle name. This API uses a promise to return the result.

**Required permissions**: ohos.permission.KILL_APP_PROCESSES or ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| clearPageStack | boolean | Yes| Whether to clear the page stack. **true** to clear, **false** otherwise.|
| appIndex | number | No | Application clone ID. The default value is **0** if this parameter is not passed. Value range: 0 to 1000. The value **0** means to terminate all processes of the main application. A value greater than 0 means to terminate all processes of the specified clone application. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 401 | If the input parameter is not valid parameter. |
| 16000050 | Internal error. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let isClearPageStack = false;
let appIndex = 1;

try {
  appManager.killProcessesByBundleName(bundleName, isClearPageStack, appIndex).then((data) => {
    console.info('killProcessesByBundleName success.');
  }).catch((err: BusinessError) => {
    console.error(`killProcessesByBundleName fail, code: ${err.code}, msg:${err.message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

## appManager.isAppRunning<sup>14+</sup>

isAppRunning(bundleName: string, appCloneIndex?: number): Promise\<boolean>

Checks whether the application with the specified bundle name and application clone index is running across all users. This API uses a promise to return the result.

> **NOTE**
>
> If the application is not installed for the current user, error code 16000073 is returned. If the application is installed for the current user, the system checks whether the application is running across all users.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| appCloneIndex | number | No | Index of the clone application. The default value is 0 if this parameter is not passed. Value range: 0 to 1000. The value 0 indicates whether the main application is running; a value greater than 0 indicates whether the specified clone application is running. |

**Return value**

| Type          | Description             |
| -------------- | ---------------- |
| Promise\<boolean> | Promise object. Returns true if at least one user is running the application with the specified bundle name and clone application index; returns false if the application with the specified bundle name and clone application index is not running under any user. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16000050 | Internal error. |
| 16000073 | The app clone index is invalid. |

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bundleName = 'ohos.samples.etsclock';
  appManager.isAppRunning(bundleName).then((data: boolean) => {
      console.info(`data: ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`isAppRunning error, code: ${err.code}, msg:${err.message}`);
    });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`isAppRunning error, code: ${code}, msg:${message}`);
}
```

## AbilityStateData<sup>14+</sup>

type AbilityStateData = _AbilityStateData.default

Defines the ability state data.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| _[AbilityStateData](js-apis-inner-application-abilityStateData.md).default | Defines the ability state information. |

## AppStateData<sup>14+</sup>

type AppStateData = _AppStateData.default

Defines the application state data.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| _[AppStateData](js-apis-inner-application-appStateData.md).default | Application state information. |

## ApplicationStateObserver<sup>14+</sup>

type ApplicationStateObserver = _ApplicationStateObserver.default

Defines the observer used to listen for application state changes.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| _[ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md).default | Application state listener. |

## ProcessInformation

type ProcessInformation = _ProcessInformation

Defines the process information.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| _[ProcessInformation](js-apis-inner-application-processInformation.md) | Process information. |

## ProcessData<sup>14+</sup>

type ProcessData = _ProcessData.default

Defines the process data.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| _[ProcessData](js-apis-inner-application-processData.md).default | Process data. |