# getProcessRunningInformation (System API)

## Modules to Import

```TypeScript
```

## getProcessRunningInformation

```TypeScript
function getProcessRunningInformation(): Promise<Array<ProcessRunningInfo>>
```

Obtains information about the running processes. This API uses a promise to return the result.

> This API is deprecated since API version 9. You are advised to use
> [appManager.getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md)

**Required permissions:** 
- API version 11 and later: N/A
- API versions 8 to 10: ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ProcessRunningInfo](arkts-ability-processrunninginfo-i.md)&gt;&gt; | Promise used to return the information about the running processes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Failed to connect to the system service; |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.getProcessRunningInformation().then((data) => {
  console.info(`The process running infos is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```


<a id="getprocessrunninginformation-1"></a>

## getProcessRunningInformation

```TypeScript
function getProcessRunningInformation(callback: AsyncCallback<Array<ProcessRunningInfo>>): void
```

Obtains information about the running processes. This API uses an asynchronous callback to return the result.

> This API is deprecated since API version 9. You are advised to use
> [appManager.getRunningProcessInformation]{
> @link @ohos.app.ability.appManager:appManager.getRunningProcessInformation()} instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md)

**Required permissions:** 
- API version 11 and later: N/A
- API versions 8 to 10: ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ProcessRunningInfo](arkts-ability-processrunninginfo-i.md)&gt;&gt; | Yes | Callback used to return the result. If the API call is successful, **err** is **undefined** and **data** is the information about the running processes. Otherwise, **err** is an error object. You can perform error handling or other custom processing. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Failed to connect to the system service; |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';

appManager.getProcessRunningInformation((error, data) => {
  if (error && error.code !== 0) {
    console.error(`GetProcessRunningInformation failed, error code: ${error.code}, error msg: ${error.message}.`);
  } else {
    console.info(`getProcessRunningInformation success, data: ${JSON.stringify(data)}`);
  }
});
```
