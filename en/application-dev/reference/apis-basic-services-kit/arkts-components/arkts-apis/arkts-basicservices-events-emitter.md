# @ohos.events.emitter(Emitter)

This module provides APIs for sending and processing events between threads in a process or within a thread. You can use the APIs of this module to subscribe to events (continuous subscription or one-shot subscription), cancel event subscription, send events to the event queue, and query the number of subscribed events. In this way, event communication between different threads in the same process and within the same thread can be implemented. It is applicable to scenarios such as cross-thread communication, module decoupling, and the event-driven mode, helping developers implement a lightweight publish-subscribe pattern, reduce coupling between components, and improve code maintainability and scalability.

Two event processing entries are provided. You can select one based on the isolation requirements:

- **Namespace APIs** (**on**, **once**, **off**, **emit**, and **getListenerCount** in the **emitter** namespace):  
provide global event subscription and publishing capabilities within a process. This entry works based on the global event queue. Any thread in the same process can subscribe to and publish events. These APIs are suitable for cross-thread event communication.

- **Instance APIs** (**Emitter** class): provide the event subscription and publishing capabilities within the  
same **Emitter** instance. Different **Emitter** instances are isolated from each other. You can create multiple independent event communication channels when events need to be isolated or grouped by instance.

**APIs used in combination**

The event communication of this module follows the calling sequence of subscription, publishing, processing, and unsubscription. For both namespace and instance APIs, you need to subscribe to an event first, and then another thread or the same thread publishes the event. The callback is executed after the event is received. When the event is no longer needed, unsubscribe from the event to release resources. In addition, event subscription has a lifecycle. Pay attention to resource management:

- **Continuous subscription** (**on**): The subscription remains valid until **off** is called to cancel  
subscription. If the subscription is not canceled, it will be retained.

- **One-shot subscription** (**once**): The subscription is automatically canceled after the event is received for  
the first time and the callback is executed. You do not need to manually call **off**.

- **Time for unsubscription**: After the subscription is canceled by calling **off**, the events that have been  
published through **emit** but have not been executed are also canceled and no callback is triggered. Note that when canceling a specified callback, you need to pass the corresponding callback function. If no callback is specified, all subscriptions to the event are canceled.

**Since:** 7

**System capability:** SystemCapability.Notification.Emitter

## Modules to Import

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [emit](arkts-basicservices-emitter-emit-f.md) | Emits a specified event. |
| [emit](arkts-basicservices-emitter-emit-f.md) | Emits a specified event. |
| [emit](arkts-basicservices-emitter-emit-f.md) | Emits a specified event. |
| [emit](arkts-basicservices-emitter-emit-f.md) | Emits an event of a specified priority. |
| [emit](arkts-basicservices-emitter-emit-f.md) | Emits an event of a specified priority. |
| [getListenerCount](arkts-basicservices-emitter-getlistenercount-f.md) | Obtains the number of subscriptions to a specified event. |
| [off](arkts-basicservices-emitter-off-f.md) | Unsubscribes from all events with the specified event ID. |
| [off](arkts-basicservices-emitter-off-f.md) | Unsubscribes from all events with the specified event ID. |
| [off](arkts-basicservices-emitter-off-f.md) | Unsubscribes from an event with the specified event ID and processed by the specified callback. This API takes effect only when **Callback\&lt;EventData&gt;** has been registered through the [on](arkts-basicservices-emitter-on-f.md) or [once](arkts-basicservices-emitter-once-f.md) API. Otherwise, no processing is performed. |
| [off](arkts-basicservices-emitter-off-f.md) | Unsubscribes from an event with the specified event ID and processed by the specified callback. This API takes effect only when **Callback\&lt;EventData&gt;** has been registered through the [on](arkts-basicservices-emitter-on-f.md) or [once](arkts-basicservices-emitter-once-f.md) API. Otherwise, no processing is performed. |
| [off](arkts-basicservices-emitter-off-f.md) | Unsubscribes from an event with the specified event ID and processed by the specified callback. This API takes effect only when **Callback\&lt;EventData&gt;** has been registered through the [on](arkts-basicservices-emitter-on-f.md) or [once](arkts-basicservices-emitter-once-f.md) API. Otherwise, no processing is performed. |
| [on](arkts-basicservices-emitter-on-f.md) | Subscribes to an event in persistent manner and executes a callback after the event is received. |
| [on](arkts-basicservices-emitter-on-f.md) | Subscribes to an event in persistent manner and executes a callback after the event is received. |
| [on](arkts-basicservices-emitter-on-f.md) | Subscribes to an event in persistent manner and executes a callback after the event is received. |
| [once](arkts-basicservices-emitter-once-f.md) | Subscribes to an event in one-shot manner and unsubscribes from it after the event callback is executed. |
| [once](arkts-basicservices-emitter-once-f.md) | Subscribes to an event in one-shot manner and unsubscribes from it after the event callback is executed. |
| [once](arkts-basicservices-emitter-once-f.md) | Subscribes to an event in one-shot manner and unsubscribes from it after the event callback is executed. |

### Classes

| Name | Description |
| --- | --- |
| [Emitter](arkts-basicservices-emitter-emitter-c.md) | This module provides the capabilities of sending and processing inter- or intra-thread events in a process of the same **Emitter** instance. You can use the following APIs to subscribe to an event in persistent or one-shot manner, cancel the subscription, or emit an event to the event queue. This module is applicable when inter-thread communication and event management are required based on independent instances. Different **Emitter** instances are isolated from each other. |

### Interfaces

| Name | Description |
| --- | --- |
| [EventData](arkts-basicservices-emitter-eventdata-i.md) | Describes data carried by the emitted event. |
| [GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md) | Describes the generic data carried by the emitted event. |
| [InnerEvent](arkts-basicservices-emitter-innerevent-i.md) | Describes an event to subscribe to or emit. The **EventPriority** settings do not take effect under event subscription. |
| [Options](arkts-basicservices-emitter-options-i.md) | Describes the event emit priority. |

### Enums

| Name | Description |
| --- | --- |
| [EventPriority](arkts-basicservices-emitter-eventpriority-e.md) | Enumerates the event priorities. |
