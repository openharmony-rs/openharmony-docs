# getUptime

## Modules to Import

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## getUptime

```TypeScript
function getUptime(timeType: TimeType, isNanoseconds?: boolean): number
```

Obtains the time elapsed since system startup. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| timeType | [TimeType](arkts-basicservices-systemdatetime-timetype-e.md) | Yes | Type of the time to be obtained. The value can only be `STARTUP` or `ACTIVE`. |
| isNanoseconds | boolean | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| number | Time elapsed since system startup. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameter types. <br> 3. Parameter verification failed. This error code was added due to missing issues.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let time: number = systemDateTime.getUptime(systemDateTime.TimeType.ACTIVE, false);
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get uptime. message: ${error.message}, code: ${error.code}`);
}
```
