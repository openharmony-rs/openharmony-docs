# subscribeToEvent

## Modules to Import

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';
```

## subscribeToEvent

```TypeScript
function subscribeToEvent(subscriber: CommonEventSubscriber, callback: Callback<CommonEventData>): Promise<void>
```

Subscribes to a common event. This API uses a promise to return the result, indicating subscription success or failure.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriber | [CommonEventSubscriber](arkts-basicservices-commoneventmanager-commoneventsubscriber-t.md) | Yes | Subscriber object. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[CommonEventData](arkts-basicservices-commoneventmanager-commoneventdata-t.md)&gt; | Yes | Callback to be invoked when a common event is subscribed to. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1500007](../errorcode-CommonEventService.md#1500007-failed-to-send-a-request-through-ipc) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-failed-to-initialize-the-common-event-service) | Failed to initialize the common event service. |
| [1500010](../errorcode-CommonEventService.md#1500010-the-number-of-subscribers-exceeds-the-upper-limit) | The count of subscriber exceeds system specification. |

**Examples**
