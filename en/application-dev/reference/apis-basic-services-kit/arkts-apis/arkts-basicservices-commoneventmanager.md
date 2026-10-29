# @ohos.commonEventManager(Common Event)

This module provides APIs to publish, subscribe to, and unsubscribe from common events. This module provides a system -level event notification mechanism that allows an app to send notifications to other apps that have subscribed to the event when the system status changes (such as power-on completion, battery level change, and screen on/off) or a custom service event occurs. This mechanism enables transferring information across components and apps.

The key concepts involved in this module are as follows:

- [Unordered common events](../../../basic-services/common-event/common-event-glossary.md#unordered-common-event):  
common events that CES forwards regardless of whether subscribers receive the events and when they subscribe to the events.  
- [Ordered common events](../../../basic-services/common-event/common-event-glossary.md#ordered-common-event):  
common events that CES forwards based on the subscriber priority. CES preferentially forwards an ordered common event to the subscriber with higher priority, waits until the subscriber receives the event, and then forwards the events to the subscriber with lower priority. Subscribers with the same priority receive common events in a random order.  
- [Sticky common events](../../../basic-services/common-event/common-event-glossary.md#sticky-common-event): common  
events that can be sent to a subscriber before or after they initiate a subscription.

**APIs used in combination**

The event communication of this module involves three processes: subscription, publishing, and ordered event. The subscription process and publishing process are associated through the event name. The publisher and subscriber do not need to be aware of each other.

**Subscription process: Create a subscriber, subscribe to an event, receive the event, and cancel the subscription.**

1. Configure the subscriber information, declare the name of the event to be subscribed to, and set the subscription
priority, publisher permission, and package name as required.
2. Create a subscriber object using **commonEventManager.createSubscriberSync**.
3. Subscribe to an event using **commonEventManager.subscribe**. When an event is published, use a callback to
receive **CommonEventData**, and process the event data in the callback.
4. Unsubscribe from the event using **commonEventManager.unsubscribe** when it is no longer needed.

**Publishing process: Publish an event (carrying data and attributes as required).**

1. Simple publishing: Publish an event by specifying only the event name using **commonEventManager.publish**.
2. Publishing with data and attributes: Configure attributes such as code, data, parameters, and **isOrdered** using  
**CommonEventPublishData**, and then call **publish** to publish the event.

**Ordered event process: Deliver the event by priority by collaborating with the subscriber.**

1. Set **isOrdered** to **true** using **CommonEventPublishData** and call **publish** to publish ordered events.
Events are delivered in sequence based on the subscriber priority.
2. The subscriber with a higher priority receives the event first, who can modify the code and data in the callback
using methods such as **setCodeAndData** for subsequent subscribers to receive.
3. After the processing is complete, call **finishCommonEvent** to deliver the event to the subscriber with the
next highest priority. To stop delivering the event, call **abortCommonEvent** to mark the event as aborted.

**Since:** 9

<!--Device-unnamed-declare namespace commonEventManager--><!--Device-unnamed-declare namespace commonEventManager-End-->

**System capability:** SystemCapability.Notification.CommonEvent

## Modules to Import

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createSubscriber](arkts-basicservices-commoneventmanager-createsubscriber-f.md#createsubscriber-1) | Creates a subscriber. This API uses an asynchronous callback to return the result. |
| [createSubscriber](arkts-basicservices-commoneventmanager-createsubscriber-f.md#createsubscriber-2) | Creates a subscriber. This API uses a promise to return the result. |
| [createSubscriberSync](arkts-basicservices-commoneventmanager-createsubscribersync-f.md#createsubscribersync-1) | Creates a subscriber synchronously. |
| [publish](arkts-basicservices-commoneventmanager-publish-f.md#publish-1) | Publishes a common event. This API uses an asynchronous callback to return the result. |
| [publish](arkts-basicservices-commoneventmanager-publish-f.md#publish-2) | Publishes a common event. This API uses an asynchronous callback to return the result. |
| [subscribe](arkts-basicservices-commoneventmanager-subscribe-f.md#subscribe-1) | Subscribes to a common event. This API uses an asynchronous callback to return the result. |
| [subscribeToEvent](arkts-basicservices-commoneventmanager-subscribetoevent-f.md#subscribetoevent-1) | Subscribes to a common event. This API uses a promise to return the result. |
| [unsubscribe](arkts-basicservices-commoneventmanager-unsubscribe-f.md#unsubscribe-1) | Unsubscribes from a common event. This API uses an asynchronous callback to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [publishAsUser](arkts-basicservices-commoneventmanager-publishasuser-f-sys.md#publishasuser-1) | Publishes a common event to a specified user. This API uses an asynchronous callback to return the result. |
| [publishAsUser](arkts-basicservices-commoneventmanager-publishasuser-f-sys.md#publishasuser-2) | Publishes a common event to a specified user and specifies the information to be published. This API uses an asynchronous callback to return the result. |
| [removeStickyCommonEvent](arkts-basicservices-commoneventmanager-removestickycommonevent-f-sys.md#removestickycommonevent-1) | Removes a [sticky common event](../../../basic-services/common-event/common-event-glossary.md#sticky-common-event). This API uses an asynchronous callback to return the result. |
| [removeStickyCommonEvent](arkts-basicservices-commoneventmanager-removestickycommonevent-f-sys.md#removestickycommonevent-2) | Removes a published [sticky common event](../../../basic-services/common-event/common-event-glossary.md#sticky-common-event). This API uses a promise to return the result. |
| [setStaticSubscriberState](arkts-basicservices-commoneventmanager-setstaticsubscriberstate-f-sys.md#setstaticsubscriberstate-1) | Enables or disables a [static subscription](../../../basic-services/common-event/common-event-glossary.md#static-subscription) event for the app. This API uses an asynchronous callback to return the result. |
| [setStaticSubscriberState](arkts-basicservices-commoneventmanager-setstaticsubscriberstate-f-sys.md#setstaticsubscriberstate-2) | Enables or disables a [static subscription](../../../basic-services/common-event/common-event-glossary.md#static-subscription) event for the app. This API uses a promise to return the result. |
| [setStaticSubscriberState](arkts-basicservices-commoneventmanager-setstaticsubscriberstate-f-sys.md#setstaticsubscriberstate-3) | Enables a [static subscription](../../../basic-services/common-event/common-event-glossary.md#static-subscription) common event for the app. This API uses a promise to return the result. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [CommonEventData](arkts-basicservices-commoneventmanager-commoneventdata-t.md) | Describes the data of a common event. |
| [CommonEventPublishData](arkts-basicservices-commoneventmanager-commoneventpublishdata-t.md) | Describes the content and properties of a common event. |
| [CommonEventSubscribeInfo](arkts-basicservices-commoneventmanager-commoneventsubscribeinfo-t.md) | Describes information about a common event subscriber. |
| [CommonEventSubscriber](arkts-basicservices-commoneventmanager-commoneventsubscriber-t.md) | Describes the subscriber of a common event. |

### Enums

| Name | Description |
| --- | --- |
| [Support](arkts-basicservices-commoneventmanager-support-e.md) | [System common events](../../../basic-services/common-event/common-event-glossary.md#system-common-event) refer to events released by system services or system apps. Subscribing to these common events requires specific permissions and event values. For details, see [System Common Events](arkts-basicservices-commoneventmanager.md). |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [Support](arkts-basicservices-commoneventmanager-support-e-sys.md) | [System common events](../../../basic-services/common-event/common-event-glossary.md#system-common-event) refer to events released by system services or system apps. Subscribing to these common events requires specific permissions and event values. For details, see [System Common Events](arkts-basicservices-commoneventmanager.md). |
<!--DelEnd-->
