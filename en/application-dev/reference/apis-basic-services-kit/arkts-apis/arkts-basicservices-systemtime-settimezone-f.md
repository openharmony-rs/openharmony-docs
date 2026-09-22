# setTimezone

## Modules to Import

```TypeScript
import { systemTime } from '@kit.BasicServicesKit';
```

## setTimezone

```TypeScript
function setTimezone(timezone: string, callback: AsyncCallback<void>): void
```

Sets the system time zone. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setTimezone](arkts-basicservices-systemdatetime-settimezone-f-sys.md)

**Required permissions:** ohos.permission.SET_TIME_ZONE

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timezone | string | Yes | System time zone to set. For details, see [Supported System Time Zones](../../../reference/apis-basic-services-kit/js-apis-system-time.md#supported-system-time-zones). |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| -1 | Parameter check failed, permission denied, or system error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemTime.setTimezone('Asia/Shanghai', (error: BusinessError) => {
    if (error) {
      console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in setting timezone.`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
}
```


<a id="settimezone-1"></a>

## setTimezone

```TypeScript
function setTimezone(timezone: string): Promise<void>
```

Sets the system time zone. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setTimezone](arkts-basicservices-systemdatetime-settimezone-f-sys.md)

**Required permissions:** ohos.permission.SET_TIME_ZONE

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timezone | string | Yes | System time zone to set. For details, see [Supported System Time Zones](../../../reference/apis-basic-services-kit/js-apis-system-time.md#supported-system-time-zones). |

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

try {
  systemTime.setTimezone('Asia/Shanghai').then(() => {
    console.info(`Succeeded in setting timezone.`);
  }).catch((error: BusinessError) => {
    console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.info(`Failed to set timezone. message: ${error.message}, code: ${error.code}`);
}
```
