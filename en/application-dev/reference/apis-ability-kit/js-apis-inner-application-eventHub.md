# EventHub

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=d7dae1423ba14ad249257c5083a18ed47fcfc6b0 translatedAt=2026-09-03T11:57:35.481Z pushedAt=2026-09-05T10:47:30.794Z -->

EventHub is an event communication mechanism based on the publish-subscribe pattern. It decouples senders and subscribers through event names, supporting efficient data transfer and state synchronization between different service modules.

It is primarily used for [data communication between UIAbility components and UI pages](../../application-models/uiability-data-sync-with-ui.md).

Different Context objects have different EventHub objects, and different EventHub objects cannot communicate directly with each other. Event subscription, unsubscription, and triggering all take effect on a specific EventHub object. When a Context object changes, its associated EventHub becomes invalid. For example, when an application creates a clone, the ApplicationContext is refreshed, and the EventHub previously created on that ApplicationContext becomes invalid.

Since Worker and TaskPool implement [multithreaded concurrency](../../arkts-utils/multi-thread-concurrency-overview.md#multithreaded-concurrency-models) through the actor model, where different virtual machine instances have exclusive memory, the EventHub object cannot be used for data communication between threads.


> **NOTE**
>
>  - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version. 
>  - The APIs of this module can be used only in the stage model.

## Constraints

- Data communication between processes through the EventHub object is not supported.
- EventHub cannot be used for data communication between Worker or TaskPool threads. Instead, use [Emitter for inter-thread communication](../../basic-services/common-event/itc-with-emitter.md).
- Data communication between EventHub objects of different Context objects within the same thread is not supported.
- A Context object converted by [sendableContextManager](js-apis-app-ability-sendableContextManager.md) is considered different from the original Context object, and data communication between their EventHub objects is not supported.

## Modules to Import

```ts
import { common } from '@kit.AbilityKit';
```

## Usage

You need to obtain an EventHub object through a Context object. The following example demonstrates how to obtain the EventHub object of a UIAbility instance's Context object.

```ts
import { common, UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  eventFunc() {
    console.info('eventFunc is called');
  }

  onCreate() {
    // Method 1 (recommended)
    this.context.eventHub.on('myEvent', this.eventFunc);

    // Method 2
    let eventhub = this.context.eventHub as common.EventHub;
    eventhub.on('myEvent', this.eventFunc);
  }
}
```

## EventHub.on

on(event: string, callback: Function): void;

Subscribes to the specified event. Before using this API, obtain an EventHub instance through the Context object.
> **NOTE**
>
> When callback is triggered by emit, the caller is the EventHub object. To change the direction of this in callback, use an arrow function.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event name.|
| callback | Function | Yes | Callback invoked when the event is triggered. The callback has no return value and can receive the parameters passed by the emit method. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example 1**
When the callback is triggered by **emit**, the invoker is the EventHub object. The EventHub object does not have the **value** property. Therefore, the result **undefined** is returned.

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  value: number = 12;

  onCreate() {
    try {
      this.context.eventHub.on('myEvent', this.eventFunc);
    } catch (e) {
      let code: number = (e as BusinessError).code;
      let msg: string = (e as BusinessError).message;
      console.error(`EventHub emit error, code: ${code}, msg: ${msg}`);
    }
  }

  onForeground() {
    try {
      // Result
      // eventFunc is called, value: undefined
      this.context.eventHub.emit('myEvent');
    } catch (e) {
      let code: number = (e as BusinessError).code;
      let msg: string = (e as BusinessError).message;
      console.error(`EventHub emit error, code: ${code}, msg: ${msg}`);
    }
  }

  eventFunc() {
    console.info(`eventFunc is called, value: ${this.value}`);
  }
}
```

**Example 2:**
When callback uses an arrow function, this points to the EntryAbility object. The EntryAbility object has the value attribute, so the result is 12.

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  value: number = 12;

  onCreate() {
    try {
      // Anonymous functions can be used to subscribe to events.
      this.context.eventHub.on('myEvent', () => {
        console.info(`anonymous eventFunc is called, value: ${this.value}`);
      });
    } catch (e) {
      let code: number = (e as BusinessError).code;
      let msg: string = (e as BusinessError).message;
      console.error(`EventHub emit error, code: ${code}, msg: ${msg}`);
    }
  }

  onForeground() {
    try {
      // Result
      // anonymous eventFunc is called, value: 12
      this.context.eventHub.emit('myEvent');
    } catch (e) {
      let code: number = (e as BusinessError).code;
      let msg: string = (e as BusinessError).message;
      console.error(`EventHub emit error, code: ${code}, msg: ${msg}`);
    }
  }

  eventFunc() {
    console.info(`eventFunc is called, value: ${this.value}`);
  }
}
```

## EventHub.off

off(event: string, callback?: Function): void;

Unsubscribes from the specified event. Before using this API, obtain an EventHub instance through the Context object.
 - If **callback** is specified, this API unsubscribes from the given event with the specified callback.
 - If **callback** is not specified, this API unsubscribes from the given event with all callbacks.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event name.|
| callback | Function | No| Callback for the event. If **callback** is unspecified, the given event with all callbacks is unsubscribed.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    try {
      this.context.eventHub.on('myEvent', this.eventFunc1);
      this.context.eventHub.off('myEvent', this.eventFunc1); // Unsubscribe from the myEvent event with the callback eventFunc1.
      this.context.eventHub.on('myEvent', this.eventFunc1);
      this.context.eventHub.on('myEvent', this.eventFunc2);
      this.context.eventHub.off('myEvent'); // Unsubscribe from the myEvent event with all the callbacks (eventFunc1 and eventFunc2).
    } catch (e) {
      let code: number = (e as BusinessError).code;
      let msg: string = (e as BusinessError).message;
      console.error(`EventHub emit error, code: ${code}, msg: ${msg}`);
    }
  }

  eventFunc1() {
    console.info('eventFunc1 is called');
  }

  eventFunc2() {
    console.info('eventFunc2 is called');
  }
}
```

## EventHub.emit

emit(event: string, ...args: Object[]): void;

Triggers the specified event. Before using this API, obtain an EventHub instance through the Context object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | string | Yes| Event name.|
| ...args | Object[] | No| Variable parameters, which are passed to the callback when the event is triggered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    this.context.eventHub.on('myEvent', this.eventFunc);
  }

  onDestroy() {
    try {
      // Result
      // eventFunc is called,undefined,undefined
      this.context.eventHub.emit('myEvent');
      // Result
      // eventFunc is called,1,undefined
      this.context.eventHub.emit('myEvent', 1);
      // Result
      // eventFunc is called,1,2
      this.context.eventHub.emit('myEvent', 1, 2);
    } catch (e) {
      let code: number = (e as BusinessError).code;
      let msg: string = (e as BusinessError).message;
      console.error(`EventHub emit error, code: ${code}, msg: ${msg}`);
    }
  }

  eventFunc(argOne: number, argTwo: number) {
    console.info(`eventFunc is called, ${argOne}, ${argTwo}`);
  }
}
```
