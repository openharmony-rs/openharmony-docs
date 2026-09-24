# clearUpApplicationData (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## clearUpApplicationData

```TypeScript
function clearUpApplicationData(bundleName: string): Promise<void>
```

Clears application data by bundle name. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CLEAN_APPLICATION_DATA

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the API call result. You can perform error handling or custom processing in this callback. |

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


<a id="clearupapplicationdata-1"></a>

## clearUpApplicationData

```TypeScript
function clearUpApplicationData(bundleName: string, callback: AsyncCallback<void>): void
```

Clears application data by bundle name. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CLEAN_APPLICATION_DATA

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the API call result. You can perform error handling or custom processing in this callback. |

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
