# publishAsUser (System API)

## Modules to Import

```TypeScript
import { commonEventManager } from '@kit.BasicServicesKit';
```

## publishAsUser

```TypeScript
function publishAsUser(event: string, userId: number, callback: AsyncCallback<void>): void
```

Publishes a common event to a specified user. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Name of the common event to publish. |
| userId | number | Yes | ID of the user who will receive the common event. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [1500003](../errorcode-CommonEventService.md#1500003-common-event-sending-frequency-is-too-high) | The common event sending frequency too high.<br>**Applicable version:** 20 and later |
| [1500006](../errorcode-CommonEventService.md#1500006-invalid-user-id) | Invalid userId.<br>**Applicable version:** 21 and later |
| [1500007](../errorcode-CommonEventService.md#1500007-failed-to-send-a-request-through-ipc) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-failed-to-initialize-the-common-event-service) | Failed to initialize the common event service. |
| [1500009](../errorcode-CommonEventService.md#1500009-failed-to-obtain-system-parameters) | Failed to obtain system parameters. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Specify the user to whom the common event will be published.
let userId = 100;

// Publish a common event.
try {
    commonEventManager.publishAsUser('event', userId, (err: BusinessError) => {
      if (err) {
        console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
        return;
      }
      console.info('publishAsUser');
    });
} catch (error) {
    let err: BusinessError = error as BusinessError;
    console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Information of the common event.
let options: commonEventManager.CommonEventPublishData = {
  code: 0,       // Initial code of the common event.
  data: 'initial data', // Initial data of the common event.
};

// Specify the user to whom the common event will be published.
let userId = 100;
// Publish a common event.
try {
  commonEventManager.publishAsUser('event', userId, options, (err: BusinessError) => {
    if (err) {
      console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info('publishAsUser');
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`publishAsUser failed, code is ${err.code}, message is ${err.message}`);
}
```


## publishAsUser

```TypeScript
function publishAsUser(
    event: string,
    userId: number,
    options: CommonEventPublishData,
    callback: AsyncCallback<void>
  ): void
```

Publishes a common event to a specified user and specifies the information to be published. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Notification.CommonEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Name of the common event to publish. |
| userId | number | Yes | ID of the user who will receive the common event. |
| options | [CommonEventPublishData](arkts-basicservices-commoneventmanager-commoneventpublishdata-t.md) | Yes | Properties of the common event to publish. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [1500003](../errorcode-CommonEventService.md#1500003-common-event-sending-frequency-is-too-high) | The common event sending frequency too high.<br>**Applicable version:** 20 and later |
| [1500006](../errorcode-CommonEventService.md#1500006-invalid-user-id) | Invalid userId.<br>**Applicable version:** 21 and later |
| [1500007](../errorcode-CommonEventService.md#1500007-failed-to-send-a-request-through-ipc) | Failed to send the message to the common event service. |
| [1500008](../errorcode-CommonEventService.md#1500008-failed-to-initialize-the-common-event-service) | Failed to initialize the common event service. |
| [1500009](../errorcode-CommonEventService.md#1500009-failed-to-obtain-system-parameters) | Failed to obtain system parameters. |

**Examples**

See [publishAsUser](#publishasuser)
