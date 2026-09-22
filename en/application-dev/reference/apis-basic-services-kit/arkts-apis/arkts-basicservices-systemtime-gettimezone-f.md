# getTimezone

## Modules to Import

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

## getTimezone

```TypeScript
function getTimezone(callback: AsyncCallback<string>): void
```

Obtains the system time zone. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getTimezone](arkts-basicservices-systemdatetime-gettimezone-f.md)(callback: AsyncCallback&lt;string&gt;)

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the system time zone. For details, see [Supported System Time Zones](../../../reference/apis-basic-services-kit/js-apis-system-time.md#supported-system-time-zones). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| -1 | Parameter check failed, permission denied, or system error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.getTimezone((error: BusinessError, data: string) => {
    if (error) {
      console.info(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in getting timezone : ${data}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
}
```


<a id="gettimezone-1"></a>

## getTimezone

```TypeScript
function getTimezone(): Promise<string>
```

Obtains the system time zone. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getTimezone](arkts-basicservices-systemdatetime-gettimezone-f.md)()

**System capability:** SystemCapability.MiscServices.Time

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the system time zone. For details, see [Supported System Time Zones](../../../reference/apis-basic-services-kit/js-apis-system-time.md#supported-system-time-zones). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| -1 | Parameter check failed, permission denied, or system error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.getTimezone().then((data: string) => {
    console.info(`Succeeded in getting timezone: ${data}`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
}
```
