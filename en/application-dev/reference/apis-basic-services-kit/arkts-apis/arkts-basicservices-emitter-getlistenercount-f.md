# getListenerCount

## Modules to Import

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## getListenerCount

```TypeScript
function getListenerCount(eventId: number | string): number
```

Obtains the number of subscriptions to a specified event.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.Emitter

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventId | number &#124; string | Yes | Event ID. The value is a string, which cannot be empty or exceed 10,240 bytes. Excess content will be truncated. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of subscriptions to a specified event. |

**Examples**

```TypeScript
let count: number = emitter.getListenerCount('eventId');
```
