# off (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## off('printerStateChange')

```TypeScript
function off(type: 'printerStateChange', callback?: Callback<boolean>): void
```

Unregisters the listener for printer state change events. This API uses a callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'printerStateChange' | Yes | Listening type. The value is fixed at **'printerStateChange'**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to return the result. The value **true** means that the operation is successful, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.off('printerStateChange', (data: boolean) => {
    console.info('off printerStateChange data : ' + JSON.stringify(data));
});
```


## off('jobStateChange')

```TypeScript
function off(type: 'jobStateChange', callback?: Callback<boolean>): void
```

Unregisters the listener for print job state change events. This API uses a callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'jobStateChange' | Yes | Listening type. The value is fixed at **'jobStateChange'**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to return the result. The value **true** means that the operation is successful, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.off('jobStateChange', (data: boolean) => {
    console.info('offJobStateChanged data : ' + JSON.stringify(data));
});
```


## off('extInfoChange')

```TypeScript
function off(type: 'extInfoChange', callback?: Callback<boolean>): void
```

Unregisters the listener for printer extension information change events. This API uses a callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'extInfoChange' | Yes | Listening type. The value is fixed at **'extInfoChange'**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | Callback used to return the result. The value **true** means that the operation is successful, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.off('extInfoChange', (data: boolean) => {
    console.info('offExtInfoChange data : ' + JSON.stringify(data));
});
```
