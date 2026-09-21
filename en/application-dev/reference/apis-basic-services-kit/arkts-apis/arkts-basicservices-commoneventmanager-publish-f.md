# publish

## Modules to Import

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';
```

## publish

```TypeScript
function publish(event: string, callback: AsyncCallback<void>): void
```

Publishes a common event. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Name of the common event to publish. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the common event is successfully published, **err** is **undefined**; if the event fails to be published, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1500003](../errorcode-CommonEventService.md#1500003-common-event-sending-frequency-is-too-high) | The common event sending frequency too high.<br>**Applicable version:** 20 and later |
| [1500007](../errorcode-CommonEventService.md#1500007-failed-to-send-a-request-through-ipc) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-failed-to-initialize-the-common-event-service) | Failed to initialize the common event service. |
| [1500009](../errorcode-CommonEventService.md#1500009-failed-to-obtain-system-parameters) | Failed to obtain system parameters. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Publish a common event.
try {
  commonEventManager.publish('event', (err: BusinessError) => {
    if (err) {
      console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`Succeeded in publishing common event.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
}
```


<a id="publish-1"></a>

## publish

```TypeScript
function publish(event: string, options: CommonEventPublishData, callback: AsyncCallback<void>): void
```

Publishes a common event. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Name of the common event to publish. |
| options | [CommonEventPublishData](arkts-basicservices-commoneventmanager-commoneventpublishdata-t.md) | Yes | Properties of the common event to publish. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the common event is successfully published, **err** is **undefined**; if the event fails to be published, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1500003](../errorcode-CommonEventService.md#1500003-common-event-sending-frequency-is-too-high) | The common event sending frequency too high.<br>**Applicable version:** 20 and later |
| [1500007](../errorcode-CommonEventService.md#1500007-failed-to-send-a-request-through-ipc) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-failed-to-initialize-the-common-event-service) | Failed to initialize the common event service. |
| [1500009](../errorcode-CommonEventService.md#1500009-failed-to-obtain-system-parameters) | Failed to obtain system parameters. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Common event information. The following uses an ordered common event as an example.
let options: commonEventManager.CommonEventPublishData = {
  code: 0,
  data: 'initial data',
  isOrdered: true // The common event is an ordered one.
};

// Publish a common event.
try {
  commonEventManager.publish('event', options, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`Succeeded in publishing common event.`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to publish common event. Code is ${err.code}, message is ${err.message}`);
}
```
