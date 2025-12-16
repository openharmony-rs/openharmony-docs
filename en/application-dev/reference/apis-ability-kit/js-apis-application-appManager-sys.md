# @ohos.application.appManager (appManager) (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->
<!--deprecated_code_no_check-->

The appManager module implements application management. You can use the APIs of this module to query whether the application is undergoing a stability test, whether the application is running on a RAM constrained device, the memory size of the application, and information about the running process.

> **NOTE**
> 
> The APIs of this module are supported since API version 8 and deprecated since API version 9. You are advised to use [@ohos.app.ability.appManager](js-apis-app-ability-appManager.md) instead. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.application.appManager (appManager)](js-apis-application-appManager.md).

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
| observer | [ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md) | Yes| Application state observer, which is used to observe the lifecycle change of an application.|

**Return value**

| Type| Description|
| --- | --- |
| number | Digital code of the observer.|

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

unregisterApplicationStateObserver(observerId: number,  callback: AsyncCallback\<void>): void

Deregisters the application state observer. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.RUNNING_STATE_OBSERVER

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| observerId | number | Yes| Numeric code of the observer.|
| callback | AsyncCallback\<void> | Yes| Callback used to return the result.|

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
| observerId | number | Yes| Numeric code of the observer.|

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

Kills a process by bundle name and account ID. This API uses a promise to return the result.

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
| accountId | number | Yes| ID of a system account. For details, see [getOsAccountCount](../apis-basic-services-kit/js-apis-osAccount.md#getcreatedosaccountscountdeprecated).|

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

Kills a process by bundle name and account ID. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is not required when **accountId** specifies the current user.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name.|
| accountId | number | Yes| ID of a system account. For details, see [getOsAccountCount](../apis-basic-services-kit/js-apis-osAccount.md#getcreatedosaccountscountdeprecated).|
| callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

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
| bundleName | string | Yes| Bundle name.|
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
| bundleName | string | Yes| Bundle name.|

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
| bundleName | string | Yes| Bundle name.|
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
| bundleName | string | Yes| Bundle name.|

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
