# @ohos.systemParameter (System Parameter) (System API)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=9dc0e26f0f6b593a4d06a056d7bca00c54ca7ef7 translatedAt=2026-09-01T08:20:08.265Z pushedAt=2026-09-01T10:59:48.785Z -->

The **SystemParameter** module provides system services with easy access to key-value pairs. You can use the APIs provided by this module to describe the service status and change the service behavior. The basic operation primitives are **get** and **set**. You can obtain the values of system parameters through getters and modify the values through setters.

For details about the system parameter design principles and definitions, see [Parameter Management](../../../device-dev/subsystems/subsys-boot-init-sysparam.md).

> **NOTE**
> - The APIs of this module are no longer maintained since API version 9. You are advised to use the new APIs of [@ohos.systemParameterEnhance](js-apis-system-parameterEnhance-sys.md) instead.
> - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module are system APIs.
> - Third-party applications cannot use the APIs provided by this module because system parameters each require specific discretionary access control (DAC) and mandatory access control (MAC) permissions.


## Modules to Import

```ts
import systemParameter from '@ohos.systemparameter';
```

## systemParameter.getSync<sup>(deprecated)</sup>

getSync(key: string, def?: string): string

Obtains a value of the specified key.

> **NOTE**
>
> Both **getSync** and **get** can be used to obtain system parameter values.
> - **getSync**: synchronous method, which directly returns the system parameter value. This method is suitable for simple synchronization scenarios.
> - **get**: asynchronous method, which uses a callback or promise to return the result asynchronously. This method is suitable for scenarios that require asynchronous processing.
>
> You should select a proper method based on the specific scenario.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be queried. |
| def | string | No | Default value of the system parameter. <br> It works only when the system parameter does not exist.<br> Its value can be **undefined** or a random character string. |

**Return value**

| Type | Description |
| -------- | -------- |
| string | Value of the system parameter.<br> If the specified key exists, the set value is returned.<br> If the specified key does not exist and **def** is set to a valid value, the set value is returned. If the specified key does not exist and **def** is set to an invalid value (such as **undefined**) or is not set, an empty string is returned. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700102 | Invalid system parameter value.                                          |
| 14700103 | The operation on the system permission is denied.                        |
| 14700104 | System internal error such as out memory or deadlock.                    |

For details about the error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
try {
  let info: string = systemParameter.getSync('const.ohos.apiversion');
  console.info(JSON.stringify(info));
} catch (e) {
  console.error('getSync unexpected error: ' + e);
}
```

## systemParameter.get<sup>(deprecated)</sup>

get(key: string, callback: AsyncCallback&lt;string&gt;): void

Obtains a value of the specified key. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Startup.SystemInfo 

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be queried. |
| callback | AsyncCallback&lt;string&gt; | Yes | Callback used to return the system parameter value asynchronously. If the operation is successful, **err** is **undefined** and **data** is the system parameter value. If the operation fails, **err** is an error object and **data** is **undefined**. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700102 | Invalid system parameter value.                                          |
| 14700103 | The operation on the system permission is denied.                        |
| 14700104 | System internal error such as out memory or deadlock.                    |

For details about the error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@ohos.base';

try {
  systemParameter.get('const.ohos.apiversion', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get system parameter. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('get const.ohos.apiversion success: ' + data);
    }
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}
```

## systemParameter.get<sup>(deprecated)</sup>

get(key: string, def: string, callback: AsyncCallback&lt;string&gt;): void

Obtains a value of the specified key. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be queried. |
| def | string | Yes | Default value of the system parameter. This parameter must be passed during the call, but its value can be a random character string. **def** takes effect only when the system parameter does not exist. |
| callback | AsyncCallback&lt;string&gt; | Yes | Callback used to return the system parameter value asynchronously. If the operation is successful, **err** is **undefined** and **data** is the system parameter value. If the operation fails, **err** is an error object and **data** is **undefined**. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700102 | Invalid system parameter value.                                          |
| 14700103 | The operation on the system permission is denied.                        |
| 14700104 | System internal error such as out memory or deadlock.                    |

For details about the error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@ohos.base';

try {
  systemParameter.get('const.ohos.apiversion', 'default', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get system parameter. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('get const.ohos.apiversion success: ' + data);
    }
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}
```

## systemParameter.get<sup>(deprecated)</sup>

get(key: string, def?: string): Promise&lt;string&gt;

Obtains a value of the specified key. This API uses a promise to return the result.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be queried. |
| def | string | No | Default value of the system parameter. <br> It works only when the system parameter does not exist. <br> Its value can be **undefined** or a random character string. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;string&gt; | Promise used to return the result. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700102 | Invalid system parameter value.                                          |
| 14700103 | The operation on the system permission is denied.                        |
| 14700104 | System internal error such as out memory or deadlock.                    |

For details about the error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@ohos.base';

try {
  let getPromise: Promise<string> = systemParameter.get('const.ohos.apiversion');
  getPromise.then((value: string) => {
    console.info('get const.ohos.apiversion success: ' + value);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get system parameter. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}
```

## systemParameter.setSync<sup>(deprecated)</sup>

setSync(key: string, value: string): void

Sets a value for the specified key.

> **NOTE**
>
> Both **setSync** and **set** can be used to set system parameter values.
> - **setSync**: synchronous method, which directly sets the system parameter and returns the result immediately. This method is suitable for simple synchronization scenarios.
> - **set**: asynchronous method, which uses a callback or promise to return the result asynchronously. This method is suitable for scenarios that require asynchronous processing.
>
> You should select a proper method based on the specific scenario.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be set. |
| value | string | Yes | Value to set. For details about length limit, see [Parameter Management](../../../device-dev/subsystems/subsys-boot-init-sysparam.md). |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700102 | Invalid system parameter value.                                          |
| 14700103 | The operation on the system permission is denied.                        |
| 14700104 | System internal error such as out memory or deadlock.                    |

For details about the error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).


**Example**

```ts
import { BusinessError } from '@ohos.base';

try {
  systemParameter.setSync('test.parameter.key', 'default');
} catch (e) {
  console.error(`Failed to set system parameter. Code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
}
```

## systemParameter.set<sup>(deprecated)</sup>

set(key: string, value: string, callback: AsyncCallback&lt;void&gt;): void

Sets a value of the specified key. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be set. |
| value | string | Yes | Value to set. For details about length limit, see [Parameter Management](../../../device-dev/subsystems/subsys-boot-init-sysparam.md). |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the setting result asynchronously. If the setting is successful, **err** is **undefined**. If the setting fails, **err** is an error object. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700102 | Invalid system parameter value.                                          |
| 14700103 | The operation on the system permission is denied.                        |
| 14700104 | System internal error such as out memory or deadlock.                    |

For details about the error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@ohos.base';

try {
  systemParameter.set('test.parameter.key', 'testValue', (err: BusinessError, data: void) => {
    if (err) {
      console.error(`Failed to set system parameter. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('set test.parameter.key value success');
    }
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}
```

## systemParameter.set<sup>(deprecated)</sup>

set(key: string, value: string): Promise&lt;void&gt;

Sets a value of the specified key. This API uses a promise to return the result.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be set. |
| value | string | Yes | Value to set. For details about length limit, see [Parameter Management](../../../device-dev/subsystems/subsys-boot-init-sysparam.md). |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700102 | Invalid system parameter value.                                          |
| 14700103 | The operation on the system permission is denied.                        |
| 14700104 | System internal error such as out memory or deadlock.                    |

For details about the error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@ohos.base';

try {
  let setPromise: Promise<void> = systemParameter.set('test.parameter.key', 'testValue');
  setPromise.then(() => {
    console.info('set test.parameter.key success');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set system parameter. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}
```
