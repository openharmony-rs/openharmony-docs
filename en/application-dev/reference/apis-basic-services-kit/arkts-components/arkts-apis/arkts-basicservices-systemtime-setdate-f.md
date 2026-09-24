# setDate

## Modules to Import

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

## setDate

```TypeScript
function setDate(date: Date, callback: AsyncCallback<void>): void
```

Sets the system date. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setDate](arkts-basicservices-systemdatetime-setdate-f-sys.md)

**Required permissions:** ohos.permission.SET_TIME

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | Date | Yes | Target date to set. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| -1 | Parameter check failed, permission denied, or system error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let date = new Date();
try {
  systemTime.setDate(date, (error: BusinessError) => {
    if (error) {
      console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in setting date.`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
}
```


<a id="setdate-1"></a>

## setDate

```TypeScript
function setDate(date: Date): Promise<void>
```

Sets the system date. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setDate](arkts-basicservices-systemdatetime-setdate-f-sys.md)

**Required permissions:** ohos.permission.SET_TIME

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | Date | Yes | Target date to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| -1 | Parameter check failed, permission denied, or system error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let date = new Date(); 
try {
  systemTime.setDate(date).then(() => {
    console.info(`Succeeded in setting date.`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set date. message: ${error.message}, code: ${error.code}`);
}
```
