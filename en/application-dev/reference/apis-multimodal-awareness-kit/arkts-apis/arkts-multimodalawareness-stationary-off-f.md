# off

## Modules to Import

```TypeScript
import { stationary } from '@kit.MultimodalAwarenessKit';
```

## off

```TypeScript
function off(activity: ActivityType, event: ActivityEvent, callback?: Callback<ActivityResponse>): void
```

Unsubscribes from the device status.

**Since:** 9

**System capability:** SystemCapability.Msdp.DeviceStatus.Stationary

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| activity | [ActivityType](arkts-multimodalawareness-stationary-activitytype-t.md) | Yes | Device status type. |
| event | [ActivityEvent](arkts-multimodalawareness-stationary-activityevent-e.md) | Yes | Event type. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ActivityResponse](arkts-multimodalawareness-stationary-activityresponse-i.md)&gt; | No | Callback used to receive reported data. If no value or **undefined** is passed, all callbacks associated with the specified event in the process will be unregistered. |

**Examples**

```TypeScript
stationary.off('still', stationary.ActivityEvent.ENTER);
```
