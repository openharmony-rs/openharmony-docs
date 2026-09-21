# get (System API)

## Modules to Import

```TypeScript
import { systemParameterEnhance } from '@kit.BasicServicesKit';
```

## get

```TypeScript
function get(key: string, callback: AsyncCallback<string>): void
```

Obtains a value of the specified key. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key to be queried. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the system parameter value asynchronously. If the operation is successful, **err** is **undefined** and **data** is the system parameter value. If the operation fails, **err** is an error object and **data** is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../errorcode-system-parameterV9.md#14700101-failure-to-query-the-system-parameter) | System parameter not found. |
| [14700103](../errorcode-device-info.md#14700103-operation-denied-due-to-permission) | The operation on the system permission is denied. |
| [14700104](../errorcode-system-parameterV9.md#14700104-internal-system-error-including-out-of-memory-and-deadlock) | System internal error such as out memory or deadlock. |

**Examples**

```TypeScript
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


<a id="get-1"></a>

## get

```TypeScript
function get(key: string, def: string, callback: AsyncCallback<string>): void
```

Obtains a value of the specified key. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key to be queried. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| def | string | Yes | Default value of the system parameter. It works only when the system parameter does not exist.<br> Its value can be a random character string. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the system parameter value asynchronously. If the operation is successful, **err** is **undefined** and **data** is the system parameter value. If the operation fails, **err** is an error object and **data** is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../errorcode-system-parameterV9.md#14700101-failure-to-query-the-system-parameter) | System parameter not found. |
| [14700103](../errorcode-device-info.md#14700103-operation-denied-due-to-permission) | The operation on the system permission is denied. |
| [14700104](../errorcode-system-parameterV9.md#14700104-internal-system-error-including-out-of-memory-and-deadlock) | System internal error such as out memory or deadlock. |

**Examples**

```TypeScript
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


<a id="get-2"></a>

## get

```TypeScript
function get(key: string, def?: string): Promise<string>
```

Obtains a value of the specified key. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key to be queried. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| def | string | No | Default value of the system parameter.<br> It works only when the system parameter does not exist. <br> Its value can be **undefined** or a random character string. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../errorcode-system-parameterV9.md#14700101-failure-to-query-the-system-parameter) | System parameter not found. |
| [14700103](../errorcode-device-info.md#14700103-operation-denied-due-to-permission) | The operation on the system permission is denied. |
| [14700104](../errorcode-system-parameterV9.md#14700104-internal-system-error-including-out-of-memory-and-deadlock) | System internal error such as out memory or deadlock. |

**Examples**

```TypeScript
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
