# getProcessRunningInfos (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## getProcessRunningInfos

```TypeScript
function getProcessRunningInfos(): Promise<Array<ProcessInformation>>
```

Obtains information about the running processes of the current application. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md)

**Required permissions:** 
- API version 11 and later: N/A
- API versions 9 to 10: ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ProcessInformation](arkts-ability-appmanager-processinformation-t.md)&gt;&gt; | Promise used to return the API call result and the process running information. You can perform error handling or custom processing in this callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed; |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.getProcessRunningInfos().then((data) => {
  console.info(`The process running infos is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```


<a id="getprocessrunninginfos-1"></a>

## getProcessRunningInfos

```TypeScript
function getProcessRunningInfos(callback: AsyncCallback<Array<ProcessInformation>>): void
```

Obtains information about the running processes of the current application. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md)

**Required permissions:** 
- API version 11 and later: N/A
- API versions 9 to 10: ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ProcessInformation](arkts-ability-appmanager-processinformation-t.md)&gt;&gt; | Yes | Callback used to return the result. If the API call is successful, **err** is **undefined** and **data** is the information about the running processes. Otherwise, **err** is an error object. You can perform error handling or other custom processing. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed; |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';

appManager.getProcessRunningInfos((error, data) => {
  if (error && error.code !== 0) {
    console.error(`getProcessRunningInfos fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`getProcessRunningInfos success, data: ${JSON.stringify(data)}`);
  }
});
```
