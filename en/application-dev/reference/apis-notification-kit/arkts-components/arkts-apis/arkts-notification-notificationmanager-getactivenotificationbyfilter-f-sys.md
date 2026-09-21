# getActiveNotificationByFilter (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## getActiveNotificationByFilter

```TypeScript
function getActiveNotificationByFilter(filter: NotificationFilter, callback: AsyncCallback<NotificationRequest>): void
```

Obtains information about the common live view that matches the specified filter criteria. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [NotificationFilter](arkts-notification-notificationmanager-notificationfilter-t-sys.md) | Yes | Filter criteria for querying the common live view. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name was not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationSubscribe } from '@kit.NotificationKit';

let bundleOption: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: notificationSubscribe.NotificationKey = {
    id: 11,
    label: ""
};
let filter: notificationManager.NotificationFilter = {
    bundle: bundleOption,
    notificationKey: notificationKey,
    extraInfoKeys: ['event']
}
let getActiveNotificationByFilterCallback = (err: BusinessError, data: notificationManager.NotificationRequest): void => {
    if (err) {
        console.error(`getActiveNotificationByFilter failed, code is ${err.code}, message is ${err.message}`);
    } else {
        console.info("getActiveNotificationByFilter success");
    }
}
notificationManager.getActiveNotificationByFilter(filter, getActiveNotificationByFilterCallback);
```


<a id="getactivenotificationbyfilter-2"></a>

## getActiveNotificationByFilter

```TypeScript
function getActiveNotificationByFilter(filter: NotificationFilter): Promise<NotificationRequest>
```

Obtains information about the common live view that matches the specified filter criteria. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [NotificationFilter](arkts-notification-notificationmanager-notificationfilter-t-sys.md) | Yes | Filter criteria for querying the common live view. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NotificationRequest](arkts-notification-notificationmanager-notificationrequest-t.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name was not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationSubscribe } from '@kit.NotificationKit';

let bundleOption: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: notificationSubscribe.NotificationKey = {
    id: 11,
    label: ""
};
let filter: notificationManager.NotificationFilter = {
    bundle: bundleOption,
    notificationKey: notificationKey,
    extraInfoKeys: ['event']
}
notificationManager.getActiveNotificationByFilter(filter).then((data: notificationManager.NotificationRequest) => {
    console.info(`getActiveNotificationByFilter success, data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getActiveNotificationByFilter failed, code is ${err.code}, message is ${err.message}`);
});
```
