# once

## Modules to Import

```TypeScript
import { stationary } from '@kit.MultimodalAwarenessKit';
```

## once

```TypeScript
function once(activity: ActivityType, callback: Callback<ActivityResponse>): void
```

Obtains the device status.

**Since:** 9

**System capability:** SystemCapability.Msdp.DeviceStatus.Stationary

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| activity | [ActivityType](arkts-multimodalawareness-stationary-activitytype-t.md) | Yes | Device status type. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ActivityResponse](arkts-multimodalawareness-stationary-activityresponse-i.md)&gt; | Yes | Callback used to receive reported data. |

**Examples**

```TypeScript
stationary.once('still', (data) => {
    console.info('data=' + JSON.stringify(data));
})
```
