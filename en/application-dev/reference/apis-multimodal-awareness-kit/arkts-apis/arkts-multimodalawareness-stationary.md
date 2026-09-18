# @ohos.stationary

The **stationary** module provides APIs to report the device status, including absolute still and relative still.

> **NOTE:** 
> 
> This module does not support x86 emulators.

**Since:** 9

**System capability:** SystemCapability.Msdp.DeviceStatus.Stationary

## Modules to Import

```TypeScript
import { stationary } from '@kit.MultimodalAwarenessKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [off](arkts-multimodalawareness-stationary-off-f.md) | Unsubscribes from the device status. |
| [on](arkts-multimodalawareness-stationary-on-f.md) | Subscribes to the device status. |
| [once](arkts-multimodalawareness-stationary-once-f.md) | Obtains the device status. |

### Interfaces

| Name | Description |
| --- | --- |
| [ActivityResponse](arkts-multimodalawareness-stationary-activityresponse-i.md) | Defines the response interface to receive the device status. |

### Enums

| Name | Description |
| --- | --- |
| [ActivityEvent](arkts-multimodalawareness-stationary-activityevent-e.md) | Enumerates the device status events. |
| [ActivityState](arkts-multimodalawareness-stationary-activitystate-e.md) | Enumerates the device statuses. |

### Types

| Name | Description |
| --- | --- |
| [ActivityType](arkts-multimodalawareness-stationary-activitytype-t.md) | Enumerates the device status types. |
