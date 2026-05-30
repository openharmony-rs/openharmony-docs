# @ohos.application.appManager (appManager)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->
<!--deprecated_code_no_check-->

The appManager module provides APIs for application management. For example, you can query whether the system is undergoing a stability test, determine whether the device is RAM-constrained, obtain the maximum memory available to the current application, and retrieve information about running processes.

> **NOTE**
> 
> The APIs of this module are supported since API version 8 and deprecated since API version 9. You are advised to use [@ohos.app.ability.appManager](js-apis-app-ability-appManager.md) instead. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import appManager from '@ohos.application.appManager';
```

## appManager.isRunningInStabilityTest

isRunningInStabilityTest(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the system is undergoing a stability test. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> A stability test scenario refers to a specific testing environment designed to verify application reliability under complex, extreme, or long-term operating conditions.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the API call result and the result indicating whether the system is undergoing a stability test. You can perform error handling or custom processing in this callback. **true** if the system is undergoing a stability test, **false** otherwise.|

**Example**
    
  ```ts
  import appManager from '@ohos.application.appManager';

  appManager.isRunningInStabilityTest((error, flag) => {
    if (error && error.code !== 0) {
      console.error(`isRunningInStabilityTest fail, error: ${JSON.stringify(error)}`);
    } else {
      console.info(`isRunningInStabilityTest success, the result is: ${JSON.stringify(flag)}`);
    }
  });
  ```


## appManager.isRunningInStabilityTest

isRunningInStabilityTest(): Promise&lt;boolean&gt;

Checks whether the system is undergoing a stability test. This API uses a promise to return the result.

> **NOTE**
>
> A stability test scenario refers to a specific testing environment designed to verify application reliability under complex, extreme, or long-term operating conditions.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

  | Type| Description| 
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise used to return the API call result and the result indicating whether the system is undergoing a stability test. You can perform error handling or custom processing in this callback. **true** if the system is undergoing a stability test, **false** otherwise.|

**Example**
    
  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  appManager.isRunningInStabilityTest().then((flag) => {
    console.info(`The result of isRunningInStabilityTest is: ${JSON.stringify(flag)}`);
  }).catch((error: BusinessError) => {
    console.error(`error: ${JSON.stringify(error)}`);
  });
  ```


## appManager.isRamConstrainedDevice<sup>7+<sup>

isRamConstrainedDevice(): Promise\<boolean>

Checks whether the current device is a RAM-constrained device (a device with severely limited memory resources). This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

  | Type| Description| 
  | -------- | -------- |
  | Promise&lt;boolean&gt; | Promise used to return the API call result and the result indicating whether the device is RAM-constrained. You can perform error handling or custom processing in this callback. **true** if the device is RAM-constrained, **false** otherwise.|

**Example**
    
  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  appManager.isRamConstrainedDevice().then((data) => {
    console.info(`The result of isRamConstrainedDevice is: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`error: ${JSON.stringify(error)}`);
  });
  ```

## appManager.isRamConstrainedDevice<sup>7+<sup>

isRamConstrainedDevice(callback: AsyncCallback\<boolean>): void

Checks whether the current device is a RAM-constrained device (a device with severely limited memory resources). This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the API call result and the result indicating whether the device is RAM-constrained. You can perform error handling or custom processing in this callback. **true** if the device is RAM-constrained, **false** otherwise.|

**Example**
    
  ```ts
  import appManager from '@ohos.application.appManager';

  appManager.isRamConstrainedDevice((error, data) => {
    if (error && error.code !== 0) {
      console.error(`isRamConstrainedDevice fail, error: ${JSON.stringify(error)}`);
    } else {
      console.info(`The result of isRamConstrainedDevice is: ${JSON.stringify(data)}`);
    }
  });
  ```

## appManager.getAppMemorySize<sup>7+<sup>

getAppMemorySize(): Promise\<number>

Obtains the maximum memory (RAM allocation) available to the current application. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

  | Type| Description| 
  | -------- | -------- |
  | Promise&lt;number&gt; | Promise used to return the maximum memory (RAM allocation) size, in MB. You can perform error processing or other custom processing based on the size.  |

**Example**
    
  ```ts
  import appManager from '@ohos.application.appManager';
  import { BusinessError } from '@ohos.base';

  appManager.getAppMemorySize().then((data) => {
    console.info(`The size of app memory is: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`error: ${JSON.stringify(error)}`);
  });
  ```

## appManager.getAppMemorySize<sup>7+<sup>

getAppMemorySize(callback: AsyncCallback\<number>): void

Obtains the maximum memory (RAM allocation) available to the current application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;number&gt; | Yes| Callback used to return the maximum memory (RAM allocation) size, in MB. You can perform error processing or other custom processing based on the size.  |

**Example**
    
  ```ts
  import appManager from '@ohos.application.appManager';

  appManager.getAppMemorySize((error, data) => {
    if (error && error.code !== 0) {
      console.error(`getAppMemorySize fail, error: ${JSON.stringify(error)}`);
    } else {
      console.info(`The size of app memory is: ${JSON.stringify(data)}`);
    }
  });
  ```
## appManager.getProcessRunningInfos<sup>(deprecated)</sup>

getProcessRunningInfos(): Promise\<Array\<ProcessRunningInfo>>

Obtains information about the running processes. This API uses a promise to return the result.

> This API is deprecated since API version 9. You are advised to use [appManager.getRunningProcessInformation](js-apis-app-ability-appManager.md#appmanagergetrunningprocessinformation) instead.

**Required permissions**: ohos.permission.GET_RUNNING_INFO (available only for system applications)

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type| Description|
| -------- | -------- |
| Promise\<Array\<[ProcessRunningInfo](js-apis-inner-application-processRunningInfo.md)>> | Promise used to return the information about the running processes.|

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

getProcessRunningInfos(callback: AsyncCallback\<Array\<ProcessRunningInfo>>): void

Obtains information about the running processes. This API uses an asynchronous callback to return the result.

> This API is deprecated since API version 9. You are advised to use [appManager.getRunningProcessInformation](js-apis-app-ability-appManager.md#appmanagergetrunningprocessinformation) instead.

**Required permissions**: ohos.permission.GET_RUNNING_INFO (available only for system applications)

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback\<Array\<[ProcessRunningInfo](js-apis-inner-application-processRunningInfo.md)>> | Yes| Callback used to return the information about the running processes.|

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
