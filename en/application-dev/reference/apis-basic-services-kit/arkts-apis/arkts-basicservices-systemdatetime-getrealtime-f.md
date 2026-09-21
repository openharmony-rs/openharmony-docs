# getRealTime

## Modules to Import

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## getRealTime

```TypeScript
function getRealTime(isNano: boolean, callback: AsyncCallback<number>): void
```

Obtains the time elapsed since system startup, including the deep sleep time. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [getUptime](arkts-basicservices-systemdatetime-getuptime-f.md)

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isNano | boolean | Yes | Whether the time to return is in nanoseconds.<br>- **true**: The result is in nanoseconds.<br>- **false**: The result is in milliseconds. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the time. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getRealTime(true, (error: BusinessError, time: number) => {
    if (error) {
      console.error(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in getting real time : ${time}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
}
```


<a id="getrealtime-1"></a>

## getRealTime

```TypeScript
function getRealTime(callback: AsyncCallback<number>): void
```

Obtains the time elapsed since system startup, including the deep sleep time. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [getUptime](arkts-basicservices-systemdatetime-getuptime-f.md)

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getRealTime((error: BusinessError, time: number) => {
    if (error) {
      console.error(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in getting real time : ${time}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
}
```


<a id="getrealtime-2"></a>

## getRealTime

```TypeScript
function getRealTime(isNano?: boolean): Promise<number>
```

Obtains the time elapsed since system startup, including the deep sleep time. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 12

**Substitutes:** [getUptime](arkts-basicservices-systemdatetime-getuptime-f.md)

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isNano | boolean | No | Whether the time to return is in nanoseconds. The default value is **false**.<br>- **true**: The result is in nanoseconds.<br>- **false**: The result is in milliseconds. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the time elapsed since system startup, including the deep sleep time. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Incorrect parameter types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getRealTime().then((time: number) => {
    console.info(`Succeeded in getting real time : ${time}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get real time. message: ${error.message}, code: ${error.code}`);
}
```
