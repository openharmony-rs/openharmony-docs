# getTime

## Modules to Import

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## getTime

```TypeScript
function getTime(isNanoseconds?: boolean): number
```

Obtains the time elapsed since the Unix epoch. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.MiscServices.Time

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isNanoseconds | boolean | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| number | Time elapsed since the Unix epoch. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let time: number = systemDateTime.getTime(true)
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get time. message: ${error.message}, code: ${error.code}`);
}
```
