# publish

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## publish

```TypeScript
function publish(request: NotificationRequest, callback: AsyncCallback<void>): void
```

Publishes a notification. This API uses an asynchronous callback to return the result.

After a notification is published, it will be displayed as a notification widget in the device's notification center, status bar, etc. If the ID and tag of the newly published notification are the same as those of an already published notification, the new notification will replace the original one, achieving a notification update effect.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md) checks whether notification is enabled for the specified application.

[cancel](arkts-notification-notificationmanager-cancel-f.md) cancels a published notification based on the notification ID and label.

[cancelAll](arkts-notification-notificationmanager-cancelall-f.md) cancels all notifications of this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md) | Yes | Content and related configuration of the notification to publish. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-notification-disabled) | Notification disabled. |
| [1600005](../errorcode-notification.md#1600005-notification-slot-disabled) | Notification slot disabled. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist.<br>**Applicable version:** 11 and later |
| [1600009](../errorcode-notification.md#1600009-notification-sending-limit-reached) | The notification sending frequency reaches the upper limit. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |
| [1600014](../errorcode-notification.md#1600014-no-related-permission) | No permission.<br>**Applicable version:** 11 and later |
| [1600015](../errorcode-notification.md#1600015-duplicate-configurations-not-allowed-for-the-current-notification-status) | The current notification status does not support duplicate configurations.<br>**Applicable version:** 11 and later |
| [1600016](../errorcode-notification.md#1600016-updated-notification-version-outdated) | The notification version for this update is too low.<br>**Applicable version:** 11 and later |
| [1600020](../errorcode-notification.md#1600020-applications-in-the-permission-control-list-are-not-allowed-to-publish-notifications) | The application is not allowed to send notifications due to permission settings.<br>**Applicable version:** 12 and later |
| [1600029](../errorcode-notification.md#1600029-failed-to-find-the-extensionability-for-the-custom-extension-area-of-the-live-view-widget) | The system failed to find the ExtensionAbility instance for the custom Live View widget template.<br>**Applicable version:** 26.0.0 and later |
| [2300007](../../apis-network-kit/errorcode-net-http.md#2300007-failed-to-connect-to-the-server) | Network unreachable.<br>**Applicable version:** 11 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// publish callback
let publishCallback = (err: BusinessError): void => {
  if (err) {
    console.error(`Failed to publish notification. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in publishing notification.`);
  }
}
// NotificationRequest object
let notificationRequest: notificationManager.NotificationRequest = {
  id: 1,
  content: {
    notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
    normal: {
      title: "test_title",
      text: "test_text",
      additionalText: "test_additionalText"
    }
  }
};
notificationManager.publish(notificationRequest, publishCallback);
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// NotificationRequest object
let notificationRequest: notificationManager.NotificationRequest = {
  id: 1,
  content: {
    notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
    normal: {
      title: "test_title",
      text: "test_text",
      additionalText: "test_additionalText"
    }
  }
};
notificationManager.publish(notificationRequest).then(() => {
  console.info(`Succeeded in publishing notification.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to publish notification. Code is ${err.code}, message is ${err.message}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// publish callback
let publishCallback = (err: BusinessError): void => {
    if (err) {
        console.error(`publish failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("publish success");
    }
}
// Use the actual user ID when calling the API.
let userId: number = 1;
// NotificationRequest object
let notificationRequest: notificationManager.NotificationRequest = {
    id: 1,
    content: {
        notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
        normal: {
            title: "test_title",
            text: "test_text",
            additionalText: "test_additionalText"
        }
    }
};
notificationManager.publish(notificationRequest, userId, publishCallback);
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let notificationRequest: notificationManager.NotificationRequest = {
    id: 1,
    content: {
        notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
        normal: {
            title: "test_title",
            text: "test_text",
            additionalText: "test_additionalText"
        }
    }
};

// Use the actual user ID when calling the API.
let userId: number = 1;

notificationManager.publish(notificationRequest, userId).then(() => {
    console.info("publish success");
}).catch((err: BusinessError) => {
    console.error(`publish failed, code is ${err.code}, message is ${err.message}`);
});
```


## publish

```TypeScript
function publish(request: NotificationRequest): Promise<void>
```

Publishes a notification. This API uses a promise to return the result.

After a notification is published, it will be displayed as a notification card in the device's notification center, status bar, and other locations. If the ID and tag of the newly published notification are the same as those of an already published notification, the new notification will replace the original one, achieving a notification update effect.

**Since:** 9

**System capability:** SystemCapability.Notification.Notification

**See also:**

[isNotificationEnabled](arkts-notification-notificationmanager-isnotificationenabled-f.md) checks whether notification is enabled for the specified application.

[cancel](arkts-notification-notificationmanager-cancel-f.md) cancels a published notification based on the notification ID and label.

[cancelAll](arkts-notification-notificationmanager-cancelall-f.md) cancels all notifications of this application.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md) | Yes | Content and related configuration of the notification to publish. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600004](../errorcode-notification.md#1600004-notification-disabled) | Notification disabled. |
| [1600005](../errorcode-notification.md#1600005-notification-slot-disabled) | Notification slot disabled. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist.<br>**Applicable version:** 11 and later |
| [1600009](../errorcode-notification.md#1600009-notification-sending-limit-reached) | The notification sending frequency reaches the upper limit. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |
| [1600014](../errorcode-notification.md#1600014-no-related-permission) | No permission.<br>**Applicable version:** 11 and later |
| [1600015](../errorcode-notification.md#1600015-duplicate-configurations-not-allowed-for-the-current-notification-status) | The current notification status does not support duplicate configurations.<br>**Applicable version:** 11 and later |
| [1600016](../errorcode-notification.md#1600016-updated-notification-version-outdated) | The notification version for this update is too low.<br>**Applicable version:** 11 and later |
| [1600020](../errorcode-notification.md#1600020-applications-in-the-permission-control-list-are-not-allowed-to-publish-notifications) | The application is not allowed to send notifications due to permission settings.<br>**Applicable version:** 12 and later |
| [1600029](../errorcode-notification.md#1600029-failed-to-find-the-extensionability-for-the-custom-extension-area-of-the-live-view-widget) | The system failed to find the ExtensionAbility instance for the custom Live View widget template.<br>**Applicable version:** 26.0.0 and later |
| [2300007](../../apis-network-kit/errorcode-net-http.md#2300007-failed-to-connect-to-the-server) | Network unreachable.<br>**Applicable version:** 11 and later |

**Examples**

See [publish](#publish)
