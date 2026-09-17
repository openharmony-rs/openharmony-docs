# isSharedBundleRunning (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## isSharedBundleRunning

```TypeScript
function isSharedBundleRunning(bundleName: string, versionCode: number): Promise<boolean>
```

Checks whether the shared library is in use. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the shared library. |
| versionCode | number | Yes | Version number of the shared library. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. **true** if the shared library is in use, **false** otherwise. |

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

const bundleName = 'com.example.myapplication';
const versionCode = 1;

appManager.isSharedBundleRunning(bundleName, versionCode).then((data) => {
  console.info(`The shared bundle running is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```

```TypeScript
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


## isSharedBundleRunning

```TypeScript
function isSharedBundleRunning(bundleName: string, versionCode: number, callback: AsyncCallback<boolean>): void
```

Checks whether the shared library is in use. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the shared library. |
| versionCode | number | Yes | Version number of the shared library. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. **true** if the shared library is in use, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

See [isSharedBundleRunning](#issharedbundlerunning)
