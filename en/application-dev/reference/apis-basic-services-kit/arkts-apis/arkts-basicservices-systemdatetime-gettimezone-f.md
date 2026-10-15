# getTimezone

## Modules to Import

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

<a id="gettimezone1"></a>

## getTimezone

```TypeScript
function getTimezone(callback: AsyncCallback<string>): void
```

Obtains the system time zone. This API uses an asynchronous callback to return the result.

**Since:** 9

<!--Device-systemDateTime-function getTimezone(callback: AsyncCallback<string>): void--><!--Device-systemDateTime-function getTimezone(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the system time zone. For details, see [Supported System Time Zones](../../../reference/apis-basic-services-kit/js-apis-date-time.md#supported-system-time-zones). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getTimezone((error: BusinessError, data: string) => {
    if (error) {
      console.error(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
      return;
    }
    console.info(`Succeeded in get timezone : ${data}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
}
```


<a id="gettimezone2"></a>

## getTimezone

```TypeScript
function getTimezone(): Promise<string>
```

Obtains the system time zone. This API uses a promise to return the result.

**Since:** 9

<!--Device-systemDateTime-function getTimezone(): Promise<string>--><!--Device-systemDateTime-function getTimezone(): Promise<string>-End-->

**System capability:** SystemCapability.MiscServices.Time

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the system time zone. For details, see [Supported System Time Zones](../../../reference/apis-basic-services-kit/js-apis-date-time.md#supported-system-time-zones). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemDateTime.getTimezone().then((data: string) => {
    console.info(`Succeeded in getting timezone: ${data}`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
  });
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get timezone. message: ${error.message}, code: ${error.code}`);
}
```
