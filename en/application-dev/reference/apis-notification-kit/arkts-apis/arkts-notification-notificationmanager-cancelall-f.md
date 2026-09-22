# cancelAll

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## cancelAll

```TypeScript
function cancelAll(callback: AsyncCallback<void>): void
```

Cancels all notifications of this application. This API uses an asynchronous callback to return the result.

After cancellation, all notifications of the current application will be removed from the notification center, status bar, and other locations, and will no longer be visible to the user. This is suitable for scenarios such as application exit or when the user manually clears all notifications.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[publish](arkts-notification-notificationmanager-publish-f.md) publishes a notification.

[cancel](arkts-notification-notificationmanager-cancel-f.md#cancel-1) cancels a published notification based on the notification ID and label.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// cancelAll callback
let cancelAllCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to cancel all notification. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in canceling all notification.`);
  }
}
notificationManager.cancelAll(cancelAllCallback);
```


<a id="cancelall-1"></a>

## cancelAll

```TypeScript
function cancelAll(): Promise<void>
```

Cancels all notifications of this application. This API uses a promise to return the result.

After cancellation, all notifications of the current application will be removed from the notification center, status bar, and other locations, and will no longer be visible to the user. This is suitable for scenarios such as application exit or when the user manually clears all notifications.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[publish](arkts-notification-notificationmanager-publish-f.md#publish-1) publishes a notification.

[cancel](arkts-notification-notificationmanager-cancel-f.md#cancel-2) cancels a notification with the specified ID.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

notificationManager.cancelAll().then(() => {
  console.info(`Succeeded in canceling all notification.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to cancel all notification. Code is ${err.code}, message is ${err.message}`);
});
```
