# isRunningInStabilityTest

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## isRunningInStabilityTest

```TypeScript
function isRunningInStabilityTest(callback: AsyncCallback<boolean>): void
```

Checks whether the system is undergoing a stability test. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> A stability test scenario refers to a specific testing environment designed to verify application reliability
> under complex, extreme, or long-term operating conditions.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the API call is successful, **err** is **undefined** and **data** is the check result for whether the system is undergoing a stability test. Otherwise, **err** is an error object. You can perform error handling or other custom processing.<br>**true** is returned if the system is undergoing a stability test; **false** is returned otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { appManager } from '@kit.AbilityKit';

appManager.isRunningInStabilityTest((err, flag) => {
  if (err) {
    console.error(`isRunningInStabilityTest fail, code: ${err.code}, msg:${err.message}`);
  } else {
    console.info(`The result of isRunningInStabilityTest is: ${JSON.stringify(flag)}`);
  }
});
```

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.isRunningInStabilityTest().then((flag) => {
  console.info(`The result of isRunningInStabilityTest is: ${JSON.stringify(flag)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```


## isRunningInStabilityTest

```TypeScript
function isRunningInStabilityTest(): Promise<boolean>
```

Checks whether the system is undergoing a stability test. This API uses a promise to return the result.

> **NOTE:** 
> 
> A stability test scenario refers to a specific testing environment designed to verify application reliability
> under complex, extreme, or long-term operating conditions.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the API call result and the result **true** or **false**. You can perform error handling or custom processing in this callback.  **true** is returned if the system is undergoing a stability test; **false** is returned otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

See [isRunningInStabilityTest](#isrunninginstabilitytest)
