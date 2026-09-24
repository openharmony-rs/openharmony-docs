# off

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## off('attachStateChange')

```TypeScript
function off(type: 'attachStateChange', callback?: Callback<AttachStateChangeInfo>): void
```

Unsubscribes from device attachment state change events.

**Since:** 20

**System capability:** SystemCapability.Mechanic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'attachStateChange' | Yes | Event type. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AttachStateChangeInfo](arkts-mechanic-mechanicmanager-attachstatechangeinfo-i.md)&gt; | No | Callback used to return the state change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |

**Examples**

```TypeScript
// Define the callback function for device connection state changes.
let callback = (result: mechanicManager.AttachStateChangeInfo) => {
  console.info(`'callback result:' ${result}`);
};

console.info('Unregister');
// Unregister the attachStateChange event listener.
mechanicManager.off("attachStateChange", callback);
console.info('Succeeded in unregistering callback.');
```


## off('trackingStateChange')

```TypeScript
function off(type: 'trackingStateChange', callback?: Callback<TrackingEventInfo>): void
```

Unsubscribes from tracking events.

**Since:** 20

**System capability:** SystemCapability.Mechanic.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'trackingStateChange' | Yes | Event type. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[TrackingEventInfo](arkts-mechanic-mechanicmanager-trackingeventinfo-i.md)&gt; | No | Callback used to return the tracking event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-system-error) | Service exception. |

**Examples**

```TypeScript
// Define the callback function for tracking state changes.
let callback = (result: mechanicManager.TrackingEventInfo) => {
  console.info(`'callback result:' ${result}`);
};

console.info('Unregister');
// Unregister the trackingStateChange event listener.
mechanicManager.off("trackingStateChange", callback);
console.info('Succeeded in unregistering callback.');
```
