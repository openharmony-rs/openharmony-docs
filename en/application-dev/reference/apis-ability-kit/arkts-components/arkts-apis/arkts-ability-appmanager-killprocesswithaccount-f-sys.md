# killProcessWithAccount (System API)

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## killProcessWithAccount

```TypeScript
function killProcessWithAccount(bundleName: string, accountId: number): Promise<void>
```

Kills a process by bundle name and account ID. This API uses a promise to return the result.

> **NOTE:** 
> 
> The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is not required when **accountId** specifies the
> current user.

**Since:** 9

**Required permissions:** 
- API version 14 and later: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES
- API versions 9 to 13: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| accountId | number | Yes | ID of a system account. For details, see [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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
let accountId = 0;

try {
  appManager.killProcessWithAccount(bundleName, accountId).then(() => {
    console.info('killProcessWithAccount success');
  }).catch((err: BusinessError) => {
    console.error(`killProcessWithAccount fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let accountId = 0;
let isClearPageStack = false;
let appIndex = 1;

try {
  appManager.killProcessWithAccount(bundleName, accountId, isClearPageStack, appIndex).then(() => {
    console.info('killProcessWithAccount success');
  }).catch((err: BusinessError) => {
    console.error(`killProcessWithAccount fail, err: ${JSON.stringify(err)}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let accountId = 0;

function killProcessWithAccountCallback(err: BusinessError) {
  if (err) {
    console.error(`killProcessWithAccountCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('killProcessWithAccountCallback success.');
  }
}

appManager.killProcessWithAccount(bundleName, accountId, killProcessWithAccountCallback);
```


## killProcessWithAccount

```TypeScript
function killProcessWithAccount(bundleName: string, accountId: number, clearPageStack: boolean, appIndex?: number):
    Promise<void>
```

Kills a process by bundle name and account ID. This API uses a promise to return the result.

> **NOTE:** 
> 
> The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is not required when **accountId** specifies the
> current user.

**Since:** 14

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| accountId | number | Yes | ID of a system account. For details, see [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |
| clearPageStack | boolean | Yes | Whether to clear the page stack. **true** to clear, **false** otherwise. |
| appIndex | number | No | Index of an application clone. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | If the input parameter is not valid parameter. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

See [killProcessWithAccount](#killprocesswithaccount)


## killProcessWithAccount

```TypeScript
function killProcessWithAccount(bundleName: string, accountId: number, callback: AsyncCallback<void>): void
```

Kills a process by bundle name and account ID. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is not required when **accountId** specifies the
> current user.

**Since:** 9

**Required permissions:** 
- API version 14 and later: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES
- API versions 9 to 13: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| accountId | number | Yes | ID of a system account. For details, see [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the API call result. You can perform error handling or custom processing in this callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

See [killProcessWithAccount](#killprocesswithaccount)
