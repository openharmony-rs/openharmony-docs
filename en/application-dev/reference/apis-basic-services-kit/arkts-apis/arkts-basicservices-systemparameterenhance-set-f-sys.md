# set (System API)

## Modules to Import

```TypeScript
import { systemParameterEnhance } from '@kit.BasicServicesKit';
```

## set

```TypeScript
function set(key: string, value: string, callback: AsyncCallback<void>): void
```

Sets a value of the specified key. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Target key. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| value | string | Yes | Value to set. The value can contain a maximum of 96 bytes (including the end character). |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../errorcode-system-parameterV9.md#14700102-invalid-system-parameter-value) | Invalid system parameter value. |
| [14700103](../errorcode-device-info.md#14700103-operation-denied-due-to-permission) | The operation on the system permission is denied. |
| [14700104](../errorcode-system-parameterV9.md#14700104-internal-system-error-including-out-of-memory-and-deadlock) | System internal error such as out memory or deadlock. |

**Examples**

```TypeScript
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

```TypeScript
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


## set

```TypeScript
function set(key: string, value: string): Promise<void>
```

Sets a value of the specified key. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Target key. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| value | string | Yes | Value to set. The value can contain a maximum of 96 bytes (including the end character). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../errorcode-system-parameterV9.md#14700102-invalid-system-parameter-value) | Invalid system parameter value. |
| [14700103](../errorcode-device-info.md#14700103-operation-denied-due-to-permission) | The operation on the system permission is denied. |
| [14700104](../errorcode-system-parameterV9.md#14700104-internal-system-error-including-out-of-memory-and-deadlock) | System internal error such as out memory or deadlock. |

**Examples**

See [set](#set)
