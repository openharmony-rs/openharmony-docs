# @ohos.events.emitter (Emitter)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

This module provides the capability of sending and processing events between threads in a process or within a thread. You can use the APIs of this module to subscribe to events (continuous subscription or one-shot subscription), cancel event subscription, send events to the event queue, and query the number of subscribed events. In this way, event communication between different threads in the same process and within the same thread can be implemented.

Two event processing entries are provided. You can select one based on the isolation requirements:

- **Namespace APIs** (**on**, **once**, **off**, **emit**, and **getListenerCount** in the **emitter** namespace): provide global event subscription and publishing capabilities within a process. This entry works based on the global event queue. Any thread in the same process can subscribe to and publish events. These APIs are suitable for cross-thread event communication.
- **Instance APIs** (**Emitter** class): provide the event subscription and publishing capabilities within the same **Emitter** instance. Different **Emitter** instances are isolated from each other. You can create multiple independent event communication channels when events need to be isolated or grouped by instance.

**APIs used in combination**

The event communication of this module follows the calling sequence of subscription, publishing, processing , and unsubscription. For both namespace and instance APIs, you need to subscribe to an event first, and then another thread or the same thread publishes the event. The callback is executed after the event is received. When the event is no longer needed, unsubscribe from the event to release resources. In addition, event subscription has a lifecycle. Pay attention to resource management:

- **Continuous subscription** (**on**): The subscription remains valid until **off** is called to cancel subscription. If the subscription is not canceled, it will be retained.
- **One-shot subscription** (**once**): The subscription is automatically canceled after the event is received for the first time and the callback is executed. You do not need to manually call **off**.
- **Time for unsubscription**: After the subscription is canceled by calling **off**, the events that have been published through **emit** but have not been executed are also canceled and no callback is triggered. Note that when canceling a specified callback, you need to pass the corresponding callback function. If no callback is specified, all subscriptions to the event are canceled.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { emitter } from '@kit.BasicServicesKit';
```

## emitter.on

on(event: InnerEvent, callback: Callback\<EventData\>): void

Subscribes to an event in persistent manner and executes a callback after the event is received.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                                                        |
| -------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| event    | [InnerEvent](#innerevent)           | Yes  | Event to subscribe to in persistent manner. The [EventPriority](#eventpriority) parameter is not required and does not take effect.|
| callback | Callback\<[EventData](#eventdata)\> | Yes  | Callback to be invoked when the event is received.                      |

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let innerEvent: emitter.InnerEvent = {
  eventId: 1
};

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};

// Execute the callback after receiving the event whose ID is 1.
emitter.on(innerEvent, callback);
```

## emitter.on<sup>11+</sup>

on(eventId: string, callback: Callback\<EventData\>): void

Subscribes to an event in persistent manner and executes a callback after the event is received.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                                  |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId    | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                      |
| callback | Callback\<[EventData](#eventdata)\> | Yes  | Callback to be invoked when the event is received.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// Execute the callback after receiving the event whose ID is eventId.
emitter.on('eventId', callback);
```

## emitter.on<sup>12+</sup>

on<T\>(eventId: string, callback: Callback\<GenericEventData<T\>\>): void

Subscribes to an event in persistent manner and executes a callback after the event is received.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                                  |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId    | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                      |
| callback | Callback\<[GenericEventData<T\>](#genericeventdatat12)\> | Yes  | Callback to be invoked when the event is received.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};
// Execute the callback after receiving the event whose event ID is eventId.
emitter.on('eventId', callback);
```

## emitter.once

once(event: InnerEvent, callback: Callback\<EventData\>): void

Subscribes to an event in one-shot manner and unsubscribes from it after the event callback is executed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                                                        |
| -------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| event    | [InnerEvent](#innerevent)           | Yes  | Event to subscribe to in one-shot manner. The [EventPriority](#eventpriority) parameter is not required and does not take effect.|
| callback | Callback\<[EventData](#eventdata)\> | Yes  | Callback to be invoked when the event is received.                      |

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let innerEvent: emitter.InnerEvent = {
  eventId: 1
};

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// Execute the callback after receiving the event whose ID is 1.
emitter.once(innerEvent, callback);
```

## emitter.once<sup>11+</sup>

once(eventId: string, callback: Callback\<EventData\>): void

Subscribes to an event in one-shot manner and unsubscribes from it after the event callback is executed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                                  |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId    | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                      |
| callback | Callback\<[EventData](#eventdata)\> | Yes  | Callback to be invoked when the event is received.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// Execute the callback after receiving the event whose event ID is eventId.
emitter.once('eventId', callback);
```

## emitter.once<sup>12+</sup>

once<T\>(eventId: string, callback: Callback\<GenericEventData<T\>\>): void

Subscribes to an event in one-shot manner and unsubscribes from it after the event callback is executed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                                  |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId    | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                      |
| callback | Callback\<[GenericEventData<T\>](#genericeventdatat12)\> | Yes  | Callback to be invoked when the event is received.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};
// Execute the callback after receiving the event whose event ID is eventId.
emitter.once('eventId', callback);
```

## emitter.off

off(eventId: number): void

Unsubscribes from all events with the specified event ID.

After this API is used to unsubscribe from an event, the event that has been published through the [emit](#emitteremit) API but has not been executed will be unsubscribed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type  | Mandatory| Description    |
| ------- | ------ | ---- | -------- |
| eventId | number | Yes  | Event ID.|

**Example**

```ts
// Unregister all callbacks for events whose **eventId** is **1**.
emitter.off(1);
```

## emitter.off<sup>11+</sup>

off(eventId: string): void

Unsubscribes from all events with the specified event ID.

After this API is used to unsubscribe from an event, the event that has been published through the [emit](#emitteremit11) API but has not been executed will be unsubscribed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type  | Mandatory| Description    |
| ------- | ------ | ---- | -------- |
| eventId | string | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.|

**Example**

```ts
// Unregister all callbacks for events whose **eventId** is **eventId1**.
emitter.off("eventId1");
```

## emitter.off<sup>10+</sup>

off(eventId: number, callback: Callback\<EventData\>): void

Unsubscribes from an event with the specified event ID and processed by the specified callback. This API takes effect only when **Callback\<EventData>** has been registered through the [on](#emitteron) or [once](#emitteronce) API. Otherwise, no processing is performed.

After this API is used to unsubscribe from an event, the event that has been published through the [emit](#emitteremit) API but has not been executed will be unsubscribed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type  | Mandatory| Description  |
| ------- | ------ | ---- | ------ |
| eventId | number | Yes  | Event ID.|
| callback | Callback\<[EventData](#eventdata)\> | Yes  | Callback to unregister, which must be the same as the callback used during registration. |

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// Unregister all callbacks for events whose **eventId** is **1**. The callback object must be the object used during registration.
// If the callback has not been registered, no processing is performed.
emitter.off(1, callback);
```

## emitter.off<sup>11+</sup>

off(eventId: string, callback: Callback\<EventData\>): void

Unsubscribes from an event with the specified event ID and processed by the specified callback. This API takes effect only when **Callback\<EventData>** has been registered through the [on](#emitteron11) or [once](#emitteronce11) API. Otherwise, no processing is performed.

After this API is used to unsubscribe from an event, the event that has been published through the [emit](#emitteremit11) API but has not been executed will be unsubscribed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                      |
| -------- | ----------------------------------- | ---- | -------------------------- |
| eventId  | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                  |
| callback | Callback\<[EventData](#eventdata)\> | Yes  | Callback to unregister, which must be the same as the callback used during registration.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// Unregister all callbacks for events whose **eventId** is **eventId1**. The callback object must be the object used during registration.
// If the callback has not been registered, no processing is performed.
emitter.off("eventId1", callback);
```

## emitter.off<sup>12+</sup>

off<T\>(eventId: string, callback: Callback\<GenericEventData<T\>\>): void

Unsubscribes from an event with the specified event ID and processed by the specified callback. This API takes effect only when **Callback\<EventData>** has been registered through the [on](#emitteron12) or [once](#emitteronce12) API. Otherwise, no processing is performed.

After this API is used to unsubscribe from an event, the event that has been published through the [emit](#emitteremit12) API but has not been executed will be unsubscribed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                      |
| -------- | ----------------------------------- | ---- | -------------------------- |
| eventId  | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                  |
| callback | Callback\<[GenericEventData<T\>](#genericeventdatat12)\> | Yes  | Callback to unregister, which must be the same as the callback used during registration.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};
// Unregister all callbacks for events whose **eventId** is **eventId1**. The callback object must be the object used during registration.
// If the callback has not been registered, no processing is performed.
emitter.off("eventId1", callback);
```

## emitter.emit

emit(event: InnerEvent, data?: EventData): void

Emits a specified event.

This API can be used to emit data objects across threads. The data objects must meet the specifications specified in [Overview of Inter-Thread Communication Objects](../../arkts-utils/serializable-overview.md). Currently, complex data decorated by decorators such as [@State](../../ui/state-management/arkts-state.md) and [@Observed](../../ui/state-management/arkts-observed-and-objectlink.md) is not supported.

After an event is published using this API, the event may not be executed immediately. When the execution starts depends on the number of events in the event queue and the execution efficiency of each event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name| Type                     | Mandatory| Description          |
| ------ | ------------------------- | ---- | ------------- |
| event  | [InnerEvent](#innerevent) | Yes  | Event to emit, where [EventPriority](#eventpriority) specifies the emit priority of the event.|
| data   | [EventData](#eventdata)   | No  | Data carried by the event. This parameter is left empty by default.|

**Example**

```ts
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

let innerEvent: emitter.InnerEvent = {
  eventId: 1,
  priority: emitter.EventPriority.HIGH
};

emitter.emit(innerEvent, eventData);
```

## emitter.emit<sup>11+</sup>

emit(eventId: string, data?: EventData): void

Emits a specified event.

This API can be used to emit data objects across threads. The data objects must meet the specifications specified in [Overview of Inter-Thread Communication Objects](../../arkts-utils/serializable-overview.md). Currently, complex data decorated by decorators such as [@State](../../ui/state-management/arkts-state.md) and [@Observed](../../ui/state-management/arkts-observed-and-objectlink.md) is not supported.

After an event is published using this API, the event may not be executed immediately. When the execution starts depends on the number of events in the event queue and the execution efficiency of each event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type                   | Mandatory| Description            |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.  |
| data    | [EventData](#eventdata) | No  | Data carried by the event. This parameter is left empty by default.|

**Example**

```ts
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

emitter.emit('eventId', eventData);
```

## emitter.emit<sup>12+</sup>

emit<T\>(eventId: string, data?: GenericEventData<T\>): void

Emits a specified event.

This API can be used to emit data objects across threads. The data objects must meet the specifications specified in [Overview of Inter-Thread Communication Objects](../../arkts-utils/serializable-overview.md). Currently, complex data decorated by decorators such as [@State](../../ui/state-management/arkts-state.md) and [@Observed](../../ui/state-management/arkts-observed-and-objectlink.md) is not supported.

After an event is published using this API, the event may not be executed immediately. When the execution starts depends on the number of events in the event queue and the execution efficiency of each event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type                   | Mandatory| Description            |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.  |
| data    | [GenericEventData<T\>](#genericeventdatat12) | No  | Data carried by the event. This parameter is left empty by default.|

**Example**

```ts
@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let eventData: emitter.GenericEventData<Sample> = {
  data: new Sample()
};
emitter.emit('eventId', eventData);
```

## emitter.emit<sup>11+</sup>

emit(eventId: string, options: Options, data?: EventData): void

Emits an event of a specified priority.

This API can be used to emit data objects across threads. The data objects must meet the specifications specified in [Overview of Inter-Thread Communication Objects](../../arkts-utils/serializable-overview.md). Currently, complex data decorated by decorators such as [@State](../../ui/state-management/arkts-state.md) and [@Observed](../../ui/state-management/arkts-observed-and-objectlink.md) is not supported.

After an event is published using this API, the event may not be executed immediately. When the execution starts depends on the number of events in the event queue and the execution efficiency of each event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type                   | Mandatory| Description            |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.  |
| options | [Options](#options11)   | Yes  | Event emit priority.    |
| data    | [EventData](#eventdata) | No  | Data carried by the event. This parameter is left empty by default.|

**Example**

```ts
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

emitter.emit('eventId', options, eventData);
```

## emitter.emit<sup>12+</sup>

emit<T\>(eventId: string, options: Options, data?: GenericEventData<T\>): void

Emits an event of a specified priority.

This API can be used to emit data objects across threads. The data objects must meet the specifications specified in [Overview of Inter-Thread Communication Objects](../../arkts-utils/serializable-overview.md). Currently, complex data decorated by decorators such as [@State](../../ui/state-management/arkts-state.md) and [@Observed](../../ui/state-management/arkts-observed-and-objectlink.md) is not supported.

After an event is published using this API, the event may not be executed immediately. When the execution starts depends on the number of events in the event queue and the execution efficiency of each event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type                   | Mandatory| Description            |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.  |
| options | [Options](#options11)   | Yes  | Event emit priority.    |
| data    | [GenericEventData<T\>](#genericeventdatat12) | No  | Data carried by the event. This parameter is left empty by default.|

**Example**

```ts
@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};
let eventData: emitter.GenericEventData<Sample> = {
  data: new Sample()
};

emitter.emit('eventId', options, eventData);
```

## emitter.getListenerCount<sup>11+</sup>

getListenerCount(eventId: number | string): number

Obtains the number of subscriptions to a specified event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type          | Mandatory| Description    |
| ------- | -------------- | ---- | -------- |
| eventId | number \| string | Yes  | Event ID.<br> The value is a string, which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.|

**Return value**

| Type    | Description        |
| ------- |------------|
| number | Number of subscriptions to a specified event.|


**Example**

```ts
let count: number = emitter.getListenerCount('eventId');
```

## EventPriority

Enumerates the event priorities.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

| Name     | Value   | Description                                               |
| --------- | ---- | --------------------------------------------------- |
| IMMEDIATE | 0    | The event will be emitted before high-priority events.                                 |
| HIGH      | 1    | The event will be emitted before low-priority events.                          |
| LOW       | 2    | The event will be emitted before idle-priority events. By default, an event is in LOW priority.    |
| IDLE      | 3    | The event will be emitted after all the other events.            |

## InnerEvent

Describes an event to subscribe to or emit. The **EventPriority** settings do not take effect under event subscription.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

| Name    | Type                       | Read Only| Optional| Description                                |
| -------- | ------------------------------- | ---- | ---- | ------------------------------ |
| eventId  | number                          | No  | No  | Event ID.|
| priority | [EventPriority](#eventpriority) | No  | Yes  | Event priority. The default value is **EventPriority.LOW**.            |

## EventData

Describes data carried by the emitted event.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Notification.Emitter

| Name| Type          | Read Only| Optional| Description          |
| ---- | ------------------ | ---- | ---- | -------------- |
| data | { [key: string]: any } | No  | Yes  | Data carried by the emitted event. The value can be in any of the following types: Array, ArrayBuffer, Boolean, DataView, Date, Error, Map, Number, Object, Primitive (except symbol), RegExp, Set, String, and TypedArray. The maximum data size is 16 MB. If the data size exceeds the limit, the event fails to be emitted.|

## Options<sup>11+</sup>

Describes the event emit priority.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Notification.Emitter

| Name    | Type                           | Read Only| Optional| Description          |
| -------- | ------------------------------- | ---- | ---- | -------------- |
| priority | [EventPriority](#eventpriority) | No  | Yes  | Event priority. The default value is **EventPriority.LOW**.|

## GenericEventData<T\><sup>12+</sup>

Describes the generic data carried by the emitted event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Notification.Emitter

| Name    | Type                           | Read Only| Optional| Description          |
| -------- | ------------------------------- | ---- | ---- | -------------- |
| data | T | No  | Yes  | Data carried by the emitted event. **T** represents a generic type, which can be customized based on service requirements.|


## Emitter<sup>22+</sup>

This module provides the capabilities of sending and processing inter- or intra-thread events in a process of the same **Emitter** instance. You can use the following APIs to subscribe to an event in persistent or one-shot manner, cancel the subscription, or emit an event to the event queue. This module is applicable when inter-thread communication and event management are required based on independent instances. Different **Emitter** instances are isolated from each other.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

### constructor<sup>22+</sup>

constructor()

Defines a constructor.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Example**


```ts
let emitter1: emitter.Emitter = new emitter.Emitter();
```

### on<sup>22+</sup>

on(eventId: string, callback: Callback\<EventData\>): void

Subscribes to an event specified by the Emitter instance in persistent manner and executes a callback after the event is received.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                                  |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId  | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                      |
| callback | Callback\<[EventData](#eventdata)\> | Yes  |  Callback to be invoked when the event is received.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let emitter1: emitter.Emitter = new emitter.Emitter();

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};

emitter1.on('eventId', callback);
```

### on<sup>22+</sup>

on<T\>(eventId: string, callback: Callback\<GenericEventData<T\>\>): void

Subscribes to an event specified by the Emitter instance in persistent manner and executes a callback after the event is received.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                                  |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId  | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                      |
| callback | Callback\<[GenericEventData<T\>](#genericeventdatat12)\> | Yes  | Callback to be invoked when the event is received.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let emitter1: emitter.Emitter = new emitter.Emitter();

@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};

emitter1.on('eventId', callback);
```

### once<sup>22+</sup>

once(eventId: string, callback: Callback\<EventData\>): void

Subscribes to an event specified by the Emitter instance in one-shot manner and unsubscribes from it after the event callback is executed. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                                  |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId  | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                      |
| callback | Callback\<[EventData](#eventdata)\> | Yes  | Callback to be invoked when the event is received.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let emitter1: emitter.Emitter = new emitter.Emitter();

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};

emitter1.once('eventId', callback);
```

### once<sup>22+</sup>

once<T\>(eventId: string, callback: Callback\<GenericEventData<T\>\>): void

Subscribes to an event specified by the Emitter instance in one-shot manner and unsubscribes from it after the event callback is executed. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                                  |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId  | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                      |
| callback | Callback\<[GenericEventData<T\>](#genericeventdatat12)\> | Yes  | Callback to be invoked when the event is received.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let emitter1: emitter.Emitter = new emitter.Emitter();

@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};

emitter1.once('eventId', callback);
```

### off<sup>22+</sup>

off(eventId: string): void

Unsubscribes from all events with the specified event ID of the Emitter instance.

After this API is used to unsubscribe from an event, the event that has been published through the [emit](#emit22) API but has not been executed will be unsubscribed.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type  | Mandatory| Description    |
| ------- | ------ | ---- | -------- |
| eventId | string | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.|

**Example**

```ts
let emitter1: emitter.Emitter = new emitter.Emitter();

emitter1.off('eventId');
```

### off<sup>22+</sup>

off(eventId: string, callback: Callback\<EventData\>): void

Unsubscribes from an event of the Emitter instance. This API takes effect only when the [on](#on22) or [once](#once22) API is used to subscribe to the event with specified event ID and a callback is used to process the event.

After this API is used to unsubscribe from an event, the event that has been published through the [emit](#emit22) API but has not been executed will be unsubscribed.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                      |
| -------- | ----------------------------------- | ---- | -------------------------- |
| eventId  | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                  |
| callback | Callback\<[EventData](#eventdata)\> | Yes  |  Callback to unregister.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

let emitter1: emitter.Emitter = new emitter.Emitter();

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};

emitter1.off('eventId', callback);
```

### off<sup>22+</sup>

off<T\>(eventId: string, callback: Callback\<GenericEventData<T\>\>): void

Unsubscribes from an event of the Emitter instance. This API takes effect only when the [on](#on22-1) or [once](#once22-1) API is used to subscribe to the event with specified event ID and a callback is used to process the event.

After this API is used to unsubscribe from an event, the event that has been published through the [emit](#emit22-1) API but has not been executed will be unsubscribed.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name  | Type                               | Mandatory| Description                      |
| -------- | ----------------------------------- | ---- | -------------------------- |
| eventId  | string                              | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.                  |
| callback | Callback\<[GenericEventData<T\>](#genericeventdatat12)\> | Yes  | Callback to unregister.|

**Example**

```ts
import { Callback } from '@kit.BasicServicesKit';

@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let emitter1: emitter.Emitter = new emitter.Emitter();

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};

emitter1.off('eventId', callback);
```

### emit<sup>22+</sup>

emit(eventId: string, data?: EventData): void

Emits a specified event to the Emitter class instance.

This API can be used to emit data objects across threads. The data objects must meet the specifications specified in [Overview of Inter-Thread Communication Objects](../../arkts-utils/serializable-overview.md). Currently, complex data decorated by decorators such as [@State](../../ui/state-management/arkts-state.md) and [@Observed](../../ui/state-management/arkts-observed-and-objectlink.md) is not supported.

After an event is published using this API, the event may not be executed immediately. When the execution starts depends on the number of events in the event queue and the execution efficiency of each event.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type                   | Mandatory| Description            |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.  |
| data    | [EventData](#eventdata) | No  | Data carried by the event. This parameter is left empty by default.|

**Example**

```ts
let emitter1: emitter.Emitter = new emitter.Emitter();
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

emitter1.emit('eventId', eventData);
```

### emit<sup>22+</sup>

emit<T\>(eventId: string, data?: GenericEventData<T\>): void

Emits a specified event to the Emitter class instance.

This API can be used to emit data objects across threads. The data objects must meet the specifications specified in [Overview of Inter-Thread Communication Objects](../../arkts-utils/serializable-overview.md). Currently, complex data decorated by decorators such as [@State](../../ui/state-management/arkts-state.md) and [@Observed](../../ui/state-management/arkts-observed-and-objectlink.md) is not supported.

After an event is published using this API, the event may not be executed immediately. When the execution starts depends on the number of events in the event queue and the execution efficiency of each event.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type                   | Mandatory| Description            |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.|
| data    | [GenericEventData<T\>](#genericeventdatat12) | No  | Data carried by the event. This parameter is left empty by default.|

**Example**

```ts
@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let emitter1: emitter.Emitter = new emitter.Emitter();

let eventData: emitter.GenericEventData<Sample> = {
  data: new Sample()
};

emitter1.emit('eventId', eventData);
```

### emit<sup>22+</sup>

emit(eventId: string, options: Options, data?: EventData): void

Emits an event of a specified priority to the Emitter instance.

This API can be used to emit data objects across threads. The data objects must meet the specifications specified in [Overview of Inter-Thread Communication Objects](../../arkts-utils/serializable-overview.md). Currently, complex data decorated by decorators such as [@State](../../ui/state-management/arkts-state.md) and [@Observed](../../ui/state-management/arkts-observed-and-objectlink.md) is not supported.

After an event is published using this API, the event may not be executed immediately. When the execution starts depends on the number of events in the event queue and the execution efficiency of each event.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type                   | Mandatory| Description            |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.  |
| options | [Options](#options11)   | Yes  | Event emit priority.    |
| data    | [EventData](#eventdata) | No  | Data carried by the event. This parameter is left empty by default.|

**Example**

```ts
let emitter1: emitter.Emitter = new emitter.Emitter();

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

emitter1.emit('eventId', options, eventData);
```

### emit<sup>22+</sup>

emit<T\>(eventId: string, options: Options, data?: GenericEventData<T\>): void

Emits an event of a specified priority to the Emitter instance.

This API can be used to emit data objects across threads. The data objects must meet the specifications specified in [Overview of Inter-Thread Communication Objects](../../arkts-utils/serializable-overview.md). Currently, complex data decorated by decorators such as [@State](../../ui/state-management/arkts-state.md) and [@Observed](../../ui/state-management/arkts-observed-and-objectlink.md) is not supported.

After an event is published using this API, the event may not be executed immediately. When the execution starts depends on the number of events in the event queue and the execution efficiency of each event.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type                   | Mandatory| Description            |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.  |
| options | [Options](#options11)   | Yes  | Event emit priority.    |
| data    | [GenericEventData<T\>](#genericeventdatat12) | No  | Data carried by the event. This parameter is left empty by default.|

**Example**

```ts
@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let emitter1: emitter.Emitter = new emitter.Emitter();

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};
let eventData: emitter.GenericEventData<Sample> = {
  data: new Sample()
};

emitter1.emit('eventId', options, eventData);
```

### getListenerCount<sup>22+</sup>

getListenerCount(eventId: string): number

Obtains the number of subscriptions to a specified event of the Emitter instance.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Notification.Emitter

**Parameters**

| Name | Type          | Mandatory| Description    |
| ------- | -------------- | ---- | -------- |
| eventId | string | Yes  | Event ID,<br>which cannot be empty or exceed 10,240 bytes. Excess content will be truncated.|

**Return value**

| Type    | Description        |
| ----- | ----- |
| number | Number of subscriptions to a specified event.|


**Example**

```ts
let emitter1: emitter.Emitter = new emitter.Emitter();
let count: number = emitter1.getListenerCount('eventId');
```
