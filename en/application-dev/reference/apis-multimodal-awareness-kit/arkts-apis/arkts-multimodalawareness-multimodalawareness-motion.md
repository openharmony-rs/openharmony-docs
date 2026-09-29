# @ohos.multimodalAwareness.motion(Motion awareness)

This module provides awareness capabilities for user motions, supporting the recognition of user gestures and motion states. It is suitable for interactive scenarios where responses are required based on user gestures or motions, such as gesture recognition and motion triggering, helping applications deliver a more natural interactive experience and precise scenario awareness.

**Since:** 15

<!--Device-unnamed-declare namespace motion--><!--Device-unnamed-declare namespace motion-End-->

**System capability:** SystemCapability.MultimodalAwareness.Motion

## Modules to Import

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getRecentOperatingHandStatus](arkts-multimodalawareness-motion-getrecentoperatinghandstatus-f.md) | Obtains the latest operating hand status. |
| [off](arkts-multimodalawareness-motion-off-f.md#offoperatinghandchanged) | Unsubscribes from operating hand change events. |
| [off](arkts-multimodalawareness-motion-off-f.md#offholdinghandchanged) | Disables listening for holding hand status changes. |
| [on](arkts-multimodalawareness-motion-on-f.md#onoperatinghandchanged) | Subscribes to operating hand awareness events. The system collects user touch data through touchscreen sensors and combines gesture recognition algorithms to determine whether the current operating hand is the left hand or the right hand. This is suitable for scenarios such as gesture interaction and single-hand or dual-hand operation adaptation, optimizing the UI layout and interaction mode by identifying the user's operating hand state. It is recommended that you call off() to unsubscribe and release resources after use, to avoid unnecessary performance and power consumption overhead. Related method: off('operatingHandChanged'): unsubscribes from operating hand awareness events. |
| [on](arkts-multimodalawareness-motion-on-f.md#onholdinghandchanged) | Subscribes to the holding hand status change awareness event. The system uses sensor data combined with recognition algorithms to determine whether the current holding hand is the left hand or the right hand. This is suitable for scenarios where reading applications, video playback, and other applications need to adjust the UI layout or functions based on the user's holding hand status. It is recommended that you call off() to unsubscribe and release resources after use to avoid unnecessary performance and power consumption overhead. Related method: off('holdingHandChanged'): unsubscribes from the holding hand status change awareness event. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [offHoverHandChange](arkts-multimodalawareness-motion-offhoverhandchange-f-sys.md) | Unsubscribe to hover hand event. |
| [offPickupChange](arkts-multimodalawareness-motion-offpickupchange-f-sys.md) | Unsubscribe to pick up sensor event. |
| [offRotateChange](arkts-multimodalawareness-motion-offrotatechange-f-sys.md) | Unsubscribe to rotate sensor event. |
| [offSmartRotateChange](arkts-multimodalawareness-motion-offsmartrotatechange-f-sys.md) | Unsubscribe to smart rotate sensor event. |
| [onHoverHandChange](arkts-multimodalawareness-motion-onhoverhandchange-f-sys.md#onhoverhandchange) | Subscribes to hover hand events and immediately starts detection for five seconds. |
| [onHoverHandChange](arkts-multimodalawareness-motion-onhoverhandchange-f-sys.md#onhoverhandchange-1) | Subscribes to hover hand events and immediately starts detection. |
| [onPickupChange](arkts-multimodalawareness-motion-onpickupchange-f-sys.md) | Subscribe to pick up sensor event. |
| [onRotateChange](arkts-multimodalawareness-motion-onrotatechange-f-sys.md) | Subscribe to rotate sensor event. |
| [onSmartRotateChange](arkts-multimodalawareness-motion-onsmartrotatechange-f-sys.md) | Subscribe to smart rotate sensor event. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [HoverHandDetectionArea](arkts-multimodalawareness-motion-hoverhanddetectionarea-i-sys.md) | The basic data structure of the hover hand detection area. |
| [SmartRotateEvent](arkts-multimodalawareness-motion-smartrotateevent-i-sys.md) | The basic data structure of the smart rotate sensor event. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [HoldingHandStatus](arkts-multimodalawareness-motion-holdinghandstatus-e.md) | Defines the holding hand state information, which represents the result of a holding hand state change awareness event. After subscribing to the event, the current holding hand state information is returned. |
| [OperatingHandStatus](arkts-multimodalawareness-motion-operatinghandstatus-e.md) | Defines the status of the operating hand. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [HoverHandAction](arkts-multimodalawareness-motion-hoverhandaction-e-sys.md) | Enum for hover hand actions. |
| [LogicalOrientation](arkts-multimodalawareness-motion-logicalorientation-e-sys.md) | Enum for logical orientation calculated by smart algorithms. |
| [PhysicalOrientation](arkts-multimodalawareness-motion-physicalorientation-e-sys.md) | Enum for physical orientation detected by the sensor. |
| [PickupEvent](arkts-multimodalawareness-motion-pickupevent-e-sys.md) | Enum for pickup event. |
| [RotateEvent](arkts-multimodalawareness-motion-rotateevent-e-sys.md) | Enum for rotate event. |
<!--DelEnd-->
