# @ohos.systemParameterEnhance (System Parameter) (System API)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b73959e1d9c45b3baa93846c25ec959748b34662 translatedAt=2026-09-01T08:21:27.951Z pushedAt=2026-09-02T05:46:15.125Z -->

System Parameter is a simple and easy-to-use key-value pair access interface provided for system services. Each system service can define system parameters to describe its status information, or change the behavior of the system service through system parameters. Its basic operation primitives are get and set. You can query the value of a system parameter through get, and modify the value of a system parameter through set. For details about the design principles and definitions of system parameters, see [System Parameter](../../../device-dev/subsystems/subsys-boot-init-sysparam.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module are system APIs.
> - Since system parameters are internal information and control parameters of each system service, each system parameter has its own DAC and MAC access control permissions. Third-party applications cannot use such APIs.

## Modules to Import

```ts
import { systemParameterEnhance } from '@kit.BasicServicesKit';
```

## systemParameterEnhance.getSync

getSync(key: string, def?: string): string

Obtains the value of the specified system parameter key.

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
| key | string | Yes | Key to be queried. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| def | string | No | Default value of the system parameter. <br> It works only when the system parameter does not exist. <br> Its value can be **undefined** or a random character string. |

**Return value**

| Type | Description |
| -------- | -------- |
| string | Value of the system parameter. If the specified key exists, the set value is returned. If the specified key does not exist and **def** is specified (not **undefined**), **def** is returned. If the specified key does not exist and **def** is not specified or **def** is **undefined**, an exception is thrown. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700101 | System parameter not found.                                          |
| 14700103 | The operation on the system permission is denied.                    |
| 14700104 | System internal error such as out memory or deadlock.                |

For details about the error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let info: string = systemParameterEnhance.getSync('const.ohos.apiversion');
  console.info('getSync result: ' + info);
} catch (e) {
  console.error(`getSync failed. Code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
}
```

## systemParameterEnhance.get

get(key: string, callback: AsyncCallback&lt;string&gt;): void

Obtains a value of the specified key. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be queried. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| callback | AsyncCallback&lt;string&gt; | Yes | Callback used to return the system parameter value asynchronously. If the operation is successful, **err** is **undefined** and **data** is the system parameter value. If the operation fails, **err** is an error object and **data** is **undefined**. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700101 | System parameter not found.                                          |
| 14700103 | The operation on the system permission is denied.                    |
| 14700104 | System internal error such as out memory or deadlock.                |

For detailed description of the above error codes, please refer to [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemParameterEnhance.get('const.ohos.apiversion', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get const.ohos.apiversion value. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`get const.ohos.apiversion value success: ${data}`);
    }
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}
```

## systemParameterEnhance.get

get(key: string, def: string, callback: AsyncCallback&lt;string&gt;): void

Obtains a value of the specified key. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be queried. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| def | string | Yes | Default value of the system parameter. It works only when the system parameter does not exist. <br> Its value can be a random character string. |
| callback | AsyncCallback&lt;string&gt; | Yes | Callback used to return the system parameter value asynchronously. If the operation is successful, **err** is **undefined** and **data** is the system parameter value. If the operation fails, **err** is an error object and **data** is **undefined**. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700101 | System parameter not found.                                          |
| 14700103 | The operation on the system permission is denied.                    |
| 14700104 | System internal error such as out memory or deadlock.                |

For details about the above error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemParameterEnhance.get('const.ohos.apiversion', 'default', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get const.ohos.apiversion value. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`get const.ohos.apiversion value success: ${data}`);
    }
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}
```

## systemParameterEnhance.get

get(key: string, def?: string): Promise&lt;string&gt;

Obtains a value of the specified key. This API uses a promise to return the result.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be queried. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| def | string | No | Default value of the system parameter. <br> It works only when the system parameter does not exist. <br> Its value can be **undefined** or a random character string. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;string&gt; | Promise used to return the result. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700101 | System parameter not found.                                          |
| 14700103 | The operation on the system permission is denied.                    |
| 14700104 | System internal error such as out memory or deadlock.                |

For details about the error codes above, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise: Promise<string> = systemParameterEnhance.get('const.ohos.apiversion');
  promise.then((value: string) => {
    console.info('get const.ohos.apiversion success: ' + value);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get const.ohos.apiversion. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}
```

## systemParameterEnhance.setSync

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
| key | string | Yes | Key to be set. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| value | string | Yes | Value to set. The value can contain a maximum of 96 bytes (including the end character). |

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
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemParameterEnhance.setSync('test.parameter.key', 'default');
} catch (e) {
  const err: BusinessError = e as BusinessError;
  console.error(`Failed to set system parameter. Code: ${err.code}, message: ${err.message}`);
}
```

## systemParameterEnhance.set

set(key: string, value: string, callback: AsyncCallback&lt;void&gt;): void

Sets a value of the specified key. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be set. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| value | string | Yes | Value to set. The value can contain a maximum of 96 bytes (including the end character). |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the system parameter value asynchronously. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| 14700102 | Invalid system parameter value.                                          |
| 14700103 | The operation on the system permission is denied.                        |
| 14700104 | System internal error such as out memory or deadlock.                    |

For details about the above error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemParameterEnhance.set('test.parameter.key', 'testValue', (err: BusinessError, data: void) => {
    if (err) {
      console.error(`Failed to set test.parameter.key value. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('set test.parameter.key value success');
    }
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}
```

## systemParameterEnhance.set

set(key: string, value: string): Promise&lt;void&gt;

Sets a value of the specified key. This API uses a promise to return the result.

**System capability**: SystemCapability.Startup.SystemInfo

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| key | string | Yes | Key to be set. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| value | string | Yes | Value to set. The value can contain a maximum of 96 bytes (including the end character). |

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

For details about the above error codes, see [System Parameter Error Codes](errorcode-system-parameterV9.md).

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise: Promise<void> = systemParameterEnhance.set('test.parameter.key', 'testValue');
  promise.then((value: void) => {
    console.info('set test.parameter.key success: ' + value);
  }).catch((err: BusinessError) => {
    console.error(`Failed to set test.parameter.key. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}
```
