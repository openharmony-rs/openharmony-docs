# killProcessesByBundleName (System API)

## Modules to Import

```TypeScript
```

## killProcessesByBundleName

```TypeScript
function killProcessesByBundleName(bundleName: string): Promise<void>
```

Kill processes by bundle name

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-f.md)

**Required permissions:** ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Examples**

```TypeScript
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


<a id="killprocessesbybundlename-1"></a>

## killProcessesByBundleName

```TypeScript
function killProcessesByBundleName(bundleName: string, callback: AsyncCallback<void>)
```

Kill processes by bundle name

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [killProcessesByBundleName](arkts-ability-appmanager-killprocessesbybundlename-f.md)

**Required permissions:** ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | bundle name. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | cut off the callback function of the account process. |

**Examples**

```TypeScript
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
