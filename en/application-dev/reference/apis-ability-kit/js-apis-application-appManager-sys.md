# @ohos.application.appManager (appManager) (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!--deprecated_code_no_check-->
<!-- md-trans-meta sourceCommit=8e4ee7947dfeb3a89be0dfff4e576f69a510a94f translatedAt=2026-09-03T10:56:04.769Z pushedAt=2026-09-05T10:47:30.501Z -->

The appManager module provides application management capabilities, including registering application state observers, obtaining foreground application information, terminating application processes, clearing application data, and obtaining running process information.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8 and deprecated since API version 9. You are advised to use [@ohos.app.ability.appManager](js-apis-app-ability-appManager.md) instead. For APIs added in later versions, the earliest API version is marked with a superscript.
>
> This page contains only the system APIs of this module. For details about other public APIs, see [@ohos.application.appManager (appManager)](js-apis-application-appManager.md).

## Modules to Import

```ts
import appManager from '@ohos.application.appManager';
```

## appManager.registerApplicationStateObserver

registerApplicationStateObserver(observer: ApplicationStateObserver): number

Registers an observer to listen for the state changes of all applications.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| observer | [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) | Yes | Application state observer used to observe the lifecycle changes of applications. |

**Return value**

| Type| Description|
| --- | --- |
| number | Numeric code of the registered observer, used to unregister the observer. |

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';

  const observerCode = appManager.registerApplicationStateObserver({
    onForegroundApplicationChanged(appStateData) {
      console.info(`onForegroundApplicationChanged, appStateData: ${appStateData}.`);
    },
    onAbilityStateChanged(abilityStateData) {
      console.info(`onAbilityStateChanged, abilityStateData: ${abilityStateData}.`);
    },
    onProcessCreated(processData) {
      console.info(`onProcessCreated, processData: ${processData}.`);
    },
    onProcessDied(processData) {
      console.info(`onProcessDied, processData: ${processData}.`);
    },
    onProcessStateChanged(processData) {
      console.info(`onProcessStateChanged, processData: ${processData}.`);
    },
    onAppStarted(appStateData) {
      console.info(`onAppStarted, appStateData: ${JSON.stringify(appStateData)}`);
    },
    onAppStopped(appStateData) {
      console.info(`onAppStopped, appStateData: ${JSON.stringify(appStateData)}`);
    }
  });
  console.info(`observerCode: ${observerCode}.`);
  ```

## appManager.unregisterApplicationStateObserver

unregisterApplicationStateObserver(observerId: number, callback: AsyncCallback\<void>): void

Deregisters the application state observer. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| observerId | number | Yes | Numeric code of the observer. |
| callback | AsyncCallback\<void> | Yes | Callback for the unregistration. |

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  let observerId = 100;

  function unregisterApplicationStateObserverCallback(err: BusinessError) {
    if (err) {
      console.error(`UnregisterApplicationStateObserverCallback failed, error code: ${err.code}, error msg: ${err.message}.`);
      return;
    }
  }

  appManager.unregisterApplicationStateObserver(observerId, unregisterApplicationStateObserverCallback);
  ```

## appManager.unregisterApplicationStateObserver

unregisterApplicationStateObserver(observerId: number): Promise\<void>

Deregisters the application state observer. This API uses a promise to return the result.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| observerId | number | Yes | Numeric code of the observer. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  let observerId = 100;

  appManager.unregisterApplicationStateObserver(observerId)
  .then((data) => {
      console.info(`unregisterApplicationStateObserver success, data: ${data}.`);
  })
  .catch((err: BusinessError) => {
      console.error(`unregisterApplicationStateObserver failed, err code: ${err.code}, err msg: ${err.message}.`);
  });
  ```

## appManager.getForegroundApplications

getForegroundApplications(callback: AsyncCallback\<Array\<AppStateData>>): void

Obtains information about the applications that are running in the foreground. The application information is defined by [AppStateData](js-apis-inner-application-appStateData.md). This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback\<Array\<[AppStateData](js-apis-inner-application-appStateData.md)>> | Yes| Callback used to return the application information.|

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';

  appManager.getForegroundApplications((err, data) => {
    if (err) {
      console.error(`GetForegroundApplications failed, error code: ${err.code}, error msg: ${err.message}.`);
    } else {
      console.info(`GetForegroundApplications success, data: ${JSON.stringify(data)}.`);
    }
  });
  ```

## appManager.getForegroundApplications

getForegroundApplications(): Promise\<Array\<AppStateData>>

Obtains information about the applications that are running in the foreground. The application information is defined by [AppStateData](js-apis-inner-application-appStateData.md). This API uses a promise to return the result.

**Required permissions**: ohos.permission.GET_RUNNING_INFO

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<[AppStateData](js-apis-inner-application-appStateData.md)>> | Promise used to return the application information.|

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  appManager.getForegroundApplications()
    .then((data) => {
      console.info(`GetForegroundApplications success, data: ${JSON.stringify(data)}.`);
    })
    .catch((err: BusinessError) => {
      console.error(`GetForegroundApplications failed, error code: ${err.code}, error msg: ${err.message}.`);
    });
  ```

## appManager.killProcessWithAccount

killProcessWithAccount(bundleName: string, accountId: number): Promise\<void\>

Terminates the application process of the specified account based on the bundle name and account ID. This API uses a promise to return the result.

> **NOTE**
>
> The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is not required when **accountId** specifies the current user.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| accountId | number | Yes | System account ID. For details, see [getCreatedOsAccountsCount](../apis-basic-services-kit/js-apis-osAccount.md#getcreatedosaccountscountdeprecated). |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Example**

```ts
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';
let accountId = 0;
appManager.killProcessWithAccount(bundleName, accountId)
  .then((data) => {
    console.info(`KillProcessWithAccount success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`KillProcessWithAccount failed, error code: ${err.code}, error msg: ${err.message}.`);
  });
```


## appManager.killProcessWithAccount

killProcessWithAccount(bundleName: string, accountId: number, callback: AsyncCallback\<void\>): void

Terminates the application process of the specified account based on the bundle name and account ID. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is not required when **accountId** specifies the current user.

**Required Permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS, ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| accountId | number | Yes | System account ID. For details, see [getCreatedOsAccountsCount](../apis-basic-services-kit/js-apis-osAccount.md#getcreatedosaccountscountdeprecated). |
| callback | AsyncCallback\<void\> | Yes | Callback function invoked when the application process of the specified account is terminated successfully. In this case, err is undefined; otherwise, it is an error object. |

**Example**

```ts
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';
let accountId = 0;

function killProcessWithAccountCallback(err: BusinessError, data: void) {
  if (err) {
    console.error(`KillProcessWithAccountCallback failed, error code: ${err.code}, error msg: ${err.message}.`);
  } else {
    console.info(`KillProcessWithAccountCallback success, data: ${JSON.stringify(data)}`);
  }
}

appManager.killProcessWithAccount(bundleName, accountId, killProcessWithAccountCallback);
```

## appManager.killProcessesByBundleName

killProcessesByBundleName(bundleName: string, callback: AsyncCallback\<void>)

Kills a process by bundle name. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes | Application bundle name. |
| callback | AsyncCallback\<void> | Yes| Callback used to return the result. If the process is killed, **err** is **undefined**; otherwise, **err** is an error object.|

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  let bundleName = 'bundleName';

  function killProcessesByBundleNameCallback(err: BusinessError, data: void) {
    if (err) {
      console.error(`KillProcessesByBundleNameCallback failed, error code: ${err.code}, error msg: ${err.message}.`);
    } else {
      console.info(`KillProcessesByBundleNameCallback success, data: ${JSON.stringify(data)}.`);
    }
  }

  appManager.killProcessesByBundleName(bundleName, killProcessesByBundleNameCallback);
  ```

## appManager.killProcessesByBundleName

killProcessesByBundleName(bundleName: string): Promise\<void>

Kills a process by bundle name. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes | Application bundle name. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  let bundleName = 'com.example.myapplication';
  appManager.killProcessesByBundleName(bundleName)
    .then((data) => {
      console.info(`KillProcessesByBundleName success, data: ${JSON.stringify(data)}.`);
    })
    .catch((err: BusinessError) => {
      console.error(`KillProcessesByBundleName failed, error code: ${err.code}, error msg: ${err.message}.`);
    });
  ```

## appManager.clearUpApplicationData

clearUpApplicationData(bundleName: string, callback: AsyncCallback\<void>)

Clears application data by bundle name. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.CLEAN_APPLICATION_DATA

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes | Application bundle name. |
| callback | AsyncCallback\<void> | Yes| Callback used to return the result. If the application data is cleared, **err** is **undefined**; otherwise, **err** is an error object.|

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  let bundleName = 'bundleName';

  function clearUpApplicationDataCallback(err: BusinessError, data: void) {
    if (err) {
      console.error(`ClearUpApplicationDataCallback failed, error code: ${err.code}, error msg: ${err.message}.`);
    } else {
      console.info(`ClearUpApplicationDataCallback success, data: ${JSON.stringify(data)}.`);
    }
  }

  appManager.clearUpApplicationData(bundleName, clearUpApplicationDataCallback);
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
| bundleName | string | Yes | Application bundle name. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<void> | Promise that returns no value.|

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  let bundleName = 'bundleName';
  appManager.clearUpApplicationData(bundleName)
    .then((data) => {
      console.info(`ClearUpApplicationData success, data: ${JSON.stringify(data)}.`);
    })
    .catch((err: BusinessError) => {
      console.error(`ClearUpApplicationData failed, error code: ${err.code}, error msg: ${err.message}.`);
    });
  ```

## appManager.getProcessRunningInformation<sup>(deprecated)</sup>

getProcessRunningInformation(): Promise\<Array\<ProcessRunningInfo>>

Obtains information about running processes. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [appManager.getRunningProcessInformation](js-apis-app-ability-appManager.md#appmanagergetrunningprocessinformation) instead.

**Required Permissions:** ohos.permission.GET_RUNNING_INFO (available only to system applications)

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Return value**

| Type | Description |
| -------- | -------- |
| Promise\<Array\<[ProcessRunningInfo](js-apis-inner-application-processRunningInfo.md)>> | Promise object used to return the information about running processes. |

**Error codes**

For details about the error codes, see [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. |

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  appManager.getProcessRunningInformation().then((data) => {
    console.info(`The process running infos is: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`error: ${JSON.stringify(error)}`);
  });
  ```

## appManager.getProcessRunningInformation<sup>(deprecated)</sup>

getProcessRunningInformation(callback: AsyncCallback\<Array\<ProcessRunningInfo>>): void

Obtains information about running processes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [appManager.getRunningProcessInformation](js-apis-app-ability-appManager.md#appmanagergetrunningprocessinformation) instead.

**Required Permissions:** ohos.permission.GET_RUNNING_INFO (available only to system applications)

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback\<Array\<[ProcessRunningInfo](js-apis-inner-application-processRunningInfo.md)>> | Yes | Callback invoked to return the information about running processes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID | Error Message |
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed. |

**Example**

  ```ts
  import appManager from '@ohos.application.appManager';

  appManager.getProcessRunningInformation((error, data) => {
    if (error && error.code !== 0) {
      console.error(`GetProcessRunningInformation failed, error code: ${error.code}, error msg: ${error.message}.`);
    } else {
      console.info(`getProcessRunningInformation success, data: ${JSON.stringify(data)}`);
    }
  });
  ```
