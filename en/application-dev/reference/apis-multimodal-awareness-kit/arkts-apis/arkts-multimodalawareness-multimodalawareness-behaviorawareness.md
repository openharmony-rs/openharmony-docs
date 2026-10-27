# @ohos.multimodalAwareness.behaviorAwareness(behaviorAwareness)

**Behavior Awareness** This module provides the MSDP device status awareness capability, user behavior data collection, sequential pattern clustering, and awareness event judgment.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace behaviorAwareness--><!--Device-unnamed-declare namespace behaviorAwareness-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [offPerception](arkts-multimodalawareness-behaviorawareness-offperception-f-sys.md#offperception-1) | The service cancels the subscription relationship on the MSDP. |
| [onPerception](arkts-multimodalawareness-behaviorawareness-onperception-f-sys.md#onperception-1) | Initiate subscription. The service side registers the subscription relationship with the MSDP and registers the awareness event callback. |
| [submitFeedback](arkts-multimodalawareness-behaviorawareness-submitfeedback-f-sys.md#submitfeedback-1) | Submit user feedback. The service side sends the user feedback to the MSDP. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ActionData](arkts-multimodalawareness-behaviorawareness-actiondata-i-sys.md) | Operation action data. |
| [BehaviorAwarenessPayload](arkts-multimodalawareness-behaviorawareness-behaviorawarenesspayload-i-sys.md) | Habit-aware domain payload. Specific data in the HABIT_Awareness domain. |
| [Coordinates](arkts-multimodalawareness-behaviorawareness-coordinates-i-sys.md) | Geographic coordinates. |
| [EventData](arkts-multimodalawareness-behaviorawareness-eventdata-i-sys.md) | Event event data. |
| [FeedbackData](arkts-multimodalawareness-behaviorawareness-feedbackdata-i-sys.md) | Feedback data. |
| [LocationAttributes](arkts-multimodalawareness-behaviorawareness-locationattributes-i-sys.md) | Location-based scenario attributes. |
| [PerceptionEvent](arkts-multimodalawareness-behaviorawareness-perceptionevent-i-sys.md) | Aware event data. Events generated after MSDP convergent awareness clustering are pushed to the service side. |
| [SubscribeInfo](arkts-multimodalawareness-behaviorawareness-subscribeinfo-i-sys.md) | Subscription Options. Defines the filter criteria for subscriptions. |
| [SystemActionAttributes](arkts-multimodalawareness-behaviorawareness-systemactionattributes-i-sys.md) | System control scenario attributes. |
| [SystemEventAttributes](arkts-multimodalawareness-behaviorawareness-systemeventattributes-i-sys.md) | System event scenario attributes. |
| [TimeAttributes](arkts-multimodalawareness-behaviorawareness-timeattributes-i-sys.md) | Time-based scenario attributes. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ActionType](arkts-multimodalawareness-behaviorawareness-actiontype-e-sys.md) | Action type enum. |
| [AdjustmentDirection](arkts-multimodalawareness-behaviorawareness-adjustmentdirection-e-sys.md) | Adjustment direction enum. |
| [BluetoothDeviceType](arkts-multimodalawareness-behaviorawareness-bluetoothdevicetype-e-sys.md) | Bluetooth device type enum. |
| [EventType](arkts-multimodalawareness-behaviorawareness-eventtype-e-sys.md) | Event type enum. |
| [FeedbackType](arkts-multimodalawareness-behaviorawareness-feedbacktype-e-sys.md) | User feedback event status type enum after an event is pushed. |
| [LocationStatusType](arkts-multimodalawareness-behaviorawareness-locationstatustype-e-sys.md) | Location status type enum. Used to distinguish entering or exiting a geofence. |
| [LocationType](arkts-multimodalawareness-behaviorawareness-locationtype-e-sys.md) | Location type enum. |
| [Operation](arkts-multimodalawareness-behaviorawareness-operation-e-sys.md) | Operation target enum. |
| [PatternType](arkts-multimodalawareness-behaviorawareness-patterntype-e-sys.md) | Perception pattern type. |
| [PerceptionDomain](arkts-multimodalawareness-behaviorawareness-perceptiondomain-e-sys.md) | Perceived domain type. It is used to distinguish different perception domains, and each domain has an independent payload structure. |
| [RecurrenceType](arkts-multimodalawareness-behaviorawareness-recurrencetype-e-sys.md) | Recurrence type enum. |
| [SoundMode](arkts-multimodalawareness-behaviorawareness-soundmode-e-sys.md) | Sound mode enum. |
<!--DelEnd-->
