# getProcessRunningInfos

## Modules to Import

```TypeScript
```

## getProcessRunningInfos

```TypeScript
function getProcessRunningInfos(): Promise<Array<ProcessRunningInfo>>
```

Obtains information about the running processes. This API uses a promise to return the result.

> This API is deprecated since API version 9. You are advised to use
> [appManager.getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md)

**Required permissions:** ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ProcessRunningInfo](arkts-ability-processrunninginfo-i.md)&gt;&gt; | Promise used to return the information about the running processes. |

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


## getProcessRunningInfos

```TypeScript
function getProcessRunningInfos(callback: AsyncCallback<Array<ProcessRunningInfo>>): void
```

Obtains information about the running processes. This API uses an asynchronous callback to return the result.

> This API is deprecated since API version 9. You are advised to use
> [appManager.getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md)

**Required permissions:** ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ProcessRunningInfo](arkts-ability-processrunninginfo-i.md)&gt;&gt; | Yes | Callback used to return the information about the running processes. |

**Examples**

See [getProcessRunningInfos](#getprocessrunninginfos)
