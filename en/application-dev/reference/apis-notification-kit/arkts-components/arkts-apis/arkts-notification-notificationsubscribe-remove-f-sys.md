# remove (System API)

## Modules to Import

```TypeScript
import { notificationSubscribe } from '@kit.NotificationKit';
```

## remove

```TypeScript
function remove(
    bundle: BundleOption,
    notificationKey: NotificationKey,
    reason: RemoveReason,
    callback: AsyncCallback<void>
  ): void
```

Removes a notification based on the bundle information and notification key. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle information of the application. |
| notificationKey | [NotificationKey](arkts-notification-notification-notificationkey-depr-i.md) | Yes | Notification key. |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | Yes | Reason for removing the notification. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name was not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationManager } from '@kit.NotificationKit';

let removeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`remove failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("remove success");
  }
}
let bundle: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: notificationSubscribe.NotificationKey = {
  id: 0,
  label: "label",
};
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CLICK_REASON_REMOVE;
notificationSubscribe.remove(bundle, notificationKey, reason, removeCallback);
```


<a id="remove-1"></a>

## remove

```TypeScript
function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>
```

Removes a notification based on the bundle information and notification key. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle information of the application. |
| notificationKey | [NotificationKey](arkts-notification-notification-notificationkey-depr-i.md) | Yes | Notification key. |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | Yes | Reason for removing the notification. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name was not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { notificationManager } from '@kit.NotificationKit';

let bundle: notificationManager.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: notificationSubscribe.NotificationKey = {
  id: 0,
  label: "label",
};
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CLICK_REASON_REMOVE;
notificationSubscribe.remove(bundle, notificationKey, reason).then(() => {
  console.info("remove success");
}).catch((err: BusinessError) => {
  console.error(`remove fail, code is ${err.code}, message is ${err.message}`);
});
```


<a id="remove-2"></a>

## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void
```

Removes a notification based on the specified unique notification ID. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hashCode | string | Yes | Unique notification ID. It is the value of **hashCode** in the [NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md) object of [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) used in the [onConsume](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md#onconsume) callback. |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | Yes | Reason for removing the notification. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let hashCode: string = 'hashCode';
let removeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`remove failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("remove success");
  }
}
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CANCEL_REASON_REMOVE;
notificationSubscribe.remove(hashCode, reason, removeCallback);
```


<a id="remove-3"></a>

## remove

```TypeScript
function remove(hashCodes: Array<String>, reason: RemoveReason, callback: AsyncCallback<void>): void
```

Removes specified notifications. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hashCodes | Array&lt;String&gt; | Yes | Array of unique notification IDs. It is the value of **hashCode** in the [NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md) object of [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) used in the [onConsume](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md#onconsume) callback. |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | Yes | Reason for removing the notification. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let hashCodes: string[] = ['hashCode1', 'hashCode2'];
let removeCallback = (err: BusinessError) => {
  if (err) {
    console.error(`remove failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info("remove success");
  }
}
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CANCEL_REASON_REMOVE;
notificationSubscribe.remove(hashCodes, reason, removeCallback);
```


<a id="remove-4"></a>

## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason): Promise<void>
```

Removes a notification based on the specified unique notification ID. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hashCode | string | Yes | Unique notification ID. It is the value of **hashCode** in the [NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md) object of [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) used in the [onConsume](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md#onconsume) callback. |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | Yes | Reason for removing the notification. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600007](../errorcode-notification.md#1600007-notification-not-found) | The notification does not exist. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let hashCode: string = 'hashCode';
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CLICK_REASON_REMOVE;
notificationSubscribe.remove(hashCode, reason).then(() => {
  console.info("remove success");
}).catch((err: BusinessError) => {
  console.error(`remove fail, code is ${err.code}, message is ${err.message}`);
});
```


<a id="remove-5"></a>

## remove

```TypeScript
function remove(hashCodes: Array<String>, reason: RemoveReason): Promise<void>
```

Removes specified notifications. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hashCodes | Array&lt;String&gt; | Yes | Array of unique notification IDs. |
| reason | [RemoveReason](arkts-notification-notificationsubscribe-removereason-e-sys.md) | Yes | Reason for removing the notification. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let hashCodes: string[] = ['hashCode1','hashCode2'];
let reason: notificationSubscribe.RemoveReason = notificationSubscribe.RemoveReason.CLICK_REASON_REMOVE;
notificationSubscribe.remove(hashCodes, reason).then(() => {
  console.info("remove success");
}).catch((err: BusinessError) => {
  console.error(`remove fail, code is ${err.code}, message is ${err.message}`);
});
```
