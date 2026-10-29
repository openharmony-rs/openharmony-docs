# cancel

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## cancel

```TypeScript
function cancel(id: number, callback: AsyncCallback<void>): void
```

Cancels a notification with the specified ID. This API uses an asynchronous callback to return the result.

After cancellation, the corresponding notification is removed from the [notification center](../../../notification/notification-glossary.md#notification-center), status bar, and other locations, and is no longer visible to the user.

Compared with [notificationManager.cancel(id, label, callback)](arkts-notification-notificationmanager-cancel-f.md), which includes the label parameter, this API does not pass in a label and will cancel the notification matching the specified ID. When a notification is published with a non-empty label, the `notificationManager.cancel(id, label, callback)` API must be used to cancel it.

**Since:** 9

<!--Device-notificationManager-function cancel(id: int, callback: AsyncCallback<void>): void--><!--Device-notificationManager-function cancel(id: int, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**See also:**

[publish](arkts-notification-notificationmanager-publish-f.md#publish-1) publishes a notification.

[cancelAll](arkts-notification-notificationmanager-cancelall-f.md#cancelall-1) cancels all notifications of this application.

[cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md) cancels notifications under a notification group of this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Notification ID, used to identify the target notification. This value is specified by the **id** field of [NotificationRequest](arkts-notification-notificationrequest-i.md) when a notification is published. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.         2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// cancel callback
let cancelCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to cancel notification. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in canceling notification.`);
  }
}
notificationManager.cancel(0, cancelCallback);
```


## cancel

```TypeScript
function cancel(id: number, label: string, callback: AsyncCallback<void>): void
```

Cancels a published notification based on the notification ID and label. This API uses an asynchronous callback to return the result.

After cancellation, the corresponding notification is removed from the [notification center](../../../notification/notification-glossary.md#notification-center), status bar, and other locations, and is no longer visible to the user. This is suitable for scenarios where a specific notification with a particular label needs to be canceled precisely.

Compared with [notificationManager.cancel(id, callback)](arkts-notification-notificationmanager-cancel-f.md), which requires only the notification ID, this API additionally has the **label** parameter, allowing precise cancellation of notifications with the same ID but different labels.

**Since:** 9

<!--Device-notificationManager-function cancel(id: int, label: string, callback: AsyncCallback<void>): void--><!--Device-notificationManager-function cancel(id: int, label: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**See also:**

[publish](arkts-notification-notificationmanager-publish-f.md#publish-1) publishes a notification.

[cancelAll](arkts-notification-notificationmanager-cancelall-f.md#cancelall-1) cancels all notifications of this application.

[cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md) cancels notifications under a notification group of this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Notification ID, used to identify the target notification. This value is specified by the **id** field of [NotificationRequest](arkts-notification-notificationrequest-i.md) when a notification is published. |
| label | string | Yes | Notification label. This value is specified by the **label** field in [NotificationRequest](arkts-notification-notificationrequest-i.md) during the notification publishment. <br> - If the **label** field is empty, the published notification that matches the specified notification ID and has an empty label is canceled. <br> - If the **label** field is not empty, the published notification that matches both the specified notification ID and label is canceled. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.         2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// cancel callback
let cancelCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to cancel notification. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in canceling notification.`);
  } 
}
notificationManager.cancel(0, 'label', cancelCallback);
```


## cancel

```TypeScript
function cancel(id: number, label?: string): Promise<void>
```

Cancels a published notification based on the notification ID and label. This API uses a promise to return the result.

After cancellation, the corresponding notification is removed from the [notification center](../../../notification/notification-glossary.md#notification-center), status bar, and other locations, and is no longer visible to the user.

**Since:** 9

<!--Device-notificationManager-function cancel(id: int, label?: string): Promise<void>--><!--Device-notificationManager-function cancel(id: int, label?: string): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**See also:**

[publish](arkts-notification-notificationmanager-publish-f.md#publish-1) publishes a notification.

[cancelAll](arkts-notification-notificationmanager-cancelall-f.md) cancels all notifications of this application.

[cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md#cancelgroup-2) cancels notifications under a notification group of this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Notification ID, used to identify the target notification. This value is specified by the id field of [NotificationRequest](arkts-notification-notificationrequest-i.md) when publishing a notification. |
| label | string | No | Notification label. The default value is empty. This value is specified by the **label** field of [NotificationRequest](arkts-notification-notificationrequest-i.md) during the notification publishment. <br> - If the **label** field is empty, the published notification that matches the specified notification ID and has an empty label is canceled. <br> - If the **label** field is not empty, the published notification that matches both the specified notification ID and label is canceled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.         2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.cancel(0).then(() => {
  console.info(`Succeeded in canceling notification.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to cancel notification. Code is ${err.code}, message is ${err.message}`);
});
```
