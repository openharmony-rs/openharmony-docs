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
| [getRecentOperatingHandStatus](arkts-multimodalawareness-motion-getrecentoperatinghandstatus-f.md#getrecentoperatinghandstatus-1) | Obtains the latest operating hand status. This method directly returns the latest operating hand status and can be called without subscribing to events. |
| [off('operatingHandChanged')](arkts-multimodalawareness-motion-off-f.md#offoperatinghandchanged) | Unsubscribes from operating hand awareness events. If off() is called without first calling on(), this method throws an exception. Related method: on('operatingHandChanged'): subscribes to operating hand awareness events. |
| [off('holdingHandChanged')](arkts-multimodalawareness-motion-off-f.md#offholdinghandchanged) | Unsubscribes from the holding hand status change awareness event. If off() is called without first calling on(), this method throws an exception. Related method: on('holdingHandChanged'): subscribes to the holding hand status change awareness event. |
| [on('operatingHandChanged')](arkts-multimodalawareness-motion-on-f.md#onoperatinghandchanged) | Subscribes to operating hand awareness events. The system collects user touch data through touchscreen sensors and combines gesture recognition algorithms to determine whether the current operating hand is the left hand or the right hand. This is suitable for scenarios such as gesture interaction and single-hand or dual-hand operation adaptation, optimizing the UI layout and interaction mode by identifying the user's operating hand state. It is recommended that you call off() to unsubscribe and release resources after use, to avoid unnecessary performance and power consumption overhead. Related method: off('operatingHandChanged'): unsubscribes from operating hand awareness events. |
| [on('holdingHandChanged')](arkts-multimodalawareness-motion-on-f.md#onholdinghandchanged) | Subscribes to the holding hand status change awareness event. The system uses sensor data combined with recognition algorithms to determine whether the current holding hand is the left hand or the right hand. This is suitable for scenarios where reading applications, video playback, and other applications need to adjust the UI layout or functions based on the user's holding hand status. It is recommended that you call off() to unsubscribe and release resources after use to avoid unnecessary performance and power consumption overhead. Related method: off('holdingHandChanged'): unsubscribes from the holding hand status change awareness event. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [offHoverHandChange](arkts-multimodalawareness-motion-offhoverhandchange-f-sys.md#offhoverhandchange-1) | Unsubscribes from the hover hand event. When the application no longer needs to monitor the hover hand event, it should call this API to cancel the subscription to release system resources. |
| [offPickupChange](arkts-multimodalawareness-motion-offpickupchange-f-sys.md#offpickupchange-1) | Unsubscribes from the pickup sensor event. This API takes effect only after onPickupChange is called to subscribe; if not subscribed, it will not take effect. When the application no longer needs to monitor the pickup event, such as page destruction, application entering the background, or pausing related functions, call this API to unsubscribe and release system resources. |
| [offRotateChange](arkts-multimodalawareness-motion-offrotatechange-f-sys.md#offrotatechange-1) | Unsubscribes from the rotation sensor event. This API takes effect only after onRotateChange is called to subscribe; if not subscribed, it will not take effect. When the application no longer needs to monitor the rotation event, such as page destruction, application entering the background, or pausing related functions, call this API to unsubscribe and release system resources. |
| [offSmartRotateChange](arkts-multimodalawareness-motion-offsmartrotatechange-f-sys.md#offsmartrotatechange-1) | Unsubscribes from the smart rotation sensor event. This API takes effect only after onSmartRotateChange is called to subscribe; if not subscribed, it will not take effect. When the application no longer needs to monitor the smart rotation event, such as page destruction, application entering the background, or pausing related functions, call this API to unsubscribe and release system resources. |
| [onHoverHandChange](arkts-multimodalawareness-motion-onhoverhandchange-f-sys.md#onhoverhandchange-1) | Subscribes to the hover hand event and immediately starts hover hand event detection, with a detection duration of five seconds. This API must be used in pairs with offHoverHandChange. After use, call offHoverHandChange to unsubscribe and release system resources. |
| [onHoverHandChange](arkts-multimodalawareness-motion-onhoverhandchange-f-sys.md#onhoverhandchange-2) | Subscribes to hover hand events and immediately starts hover hand event detection, with a configurable detection duration. This API must be used in pair with offHoverHandChange. After use, call offHoverHandChange to unsubscribe and release system resources. |
| [onPickupChange](arkts-multimodalawareness-motion-onpickupchange-f-sys.md#onpickupchange-1) | Subscribes to pickup sensor events. This event is triggered and the callback is invoked when the system detects that the device is picked up. It can be used to trigger scenarios such as smart wake-up. This API must be used in pair with offPickupChange. After use, call offPickupChange to unsubscribe and release system resources. |
| [onRotateChange](arkts-multimodalawareness-motion-onrotatechange-f-sys.md#onrotatechange-1) | Subscribes to rotation sensor events. This event is triggered and the callback is invoked when the device rotates and causes an orientation change. It is used when implementing functions such as adaptive screen orientation. This API must be used in pair with offRotateChange. After use, call offRotateChange to unsubscribe and release system resources. |
| [onSmartRotateChange](arkts-multimodalawareness-motion-onsmartrotatechange-f-sys.md#onsmartrotatechange-1) | Subscribes to smart rotation sensor events. This event is triggered and the callback is invoked when the physical orientation of the device changes or the smart algorithm adjusts the logical orientation. It is used when implementing scenarios such as smart screen rotation. This API must be used in pair with offSmartRotateChange. After use, call offSmartRotateChange to unsubscribe and release system resources. |
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
