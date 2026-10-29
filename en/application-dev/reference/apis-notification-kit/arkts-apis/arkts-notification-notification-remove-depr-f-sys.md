# remove (System API)

## Modules to Import

```TypeScript
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

Removes a notification for a specified bundle. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-1)(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(    bundle: BundleOption,    notificationKey: NotificationKey,    reason: RemoveReason,    callback: AsyncCallback<void>  ): void--><!--Device-notification-function remove(    bundle: BundleOption,    notificationKey: NotificationKey,    reason: RemoveReason,    callback: AsyncCallback<void>  ): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle information of the application. |
| notificationKey | [NotificationKey](arkts-notification-notification-notificationkey-depr-i.md) | Yes | Notification key. |
| reason | RemoveReason | Yes | Reason for notification deletion. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let removeCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("remove failed " + JSON.stringify(err));
  } else {
    console.info("remove success");
  }
}
let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: Notification.NotificationKey = {
  id: 0,
  label: "label",
};
let reason: Notification.RemoveReason = Notification.RemoveReason.CLICK_REASON_REMOVE;
Notification.remove(bundle, notificationKey, reason, removeCallback);
```

<!--DelEnd-->


## remove

```TypeScript
function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>
```

Removes a notification for a specified bundle. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-2)(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>--><!--Device-notification-function remove(bundle: BundleOption, notificationKey: NotificationKey, reason: RemoveReason): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle information of the application. |
| notificationKey | [NotificationKey](arkts-notification-notification-notificationkey-depr-i.md) | Yes | Notification key. |
| reason | RemoveReason | Yes | Reason for notification deletion. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
let notificationKey: Notification.NotificationKey = {
  id: 0,
  label: "label",
};
let reason: Notification.RemoveReason = Notification.RemoveReason.CLICK_REASON_REMOVE;
Notification.remove(bundle, notificationKey, reason).then(() => {
  console.info("remove success");
}).catch((err: Base.BusinessError) => {
  console.error(`remove failed, code is ${err}`);
});
```

<!--DelEnd-->


## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void
```

Removes a notification for a specified bundle. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-3)(hashCode: string, reason: RemoveReason, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void--><!--Device-notification-function remove(hashCode: string, reason: RemoveReason, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hashCode | string | Yes | Unique notification ID. It is the value of **hashCode** in the [NotificationRequest](arkts-notification-notificationrequest-i.md) object of [SubscribeCallbackData](arkts-notification-notificationsubscriber-subscribecallbackdata-i-sys.md) used in the [onConsume](arkts-notification-notificationsubscriber-i-sys.md#onconsume) callback. |
| reason | RemoveReason | Yes | Reason for notification deletion. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let hashCode: string = 'hashCode';

let removeCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("remove failed " + JSON.stringify(err));
  } else {
    console.info("remove success");
  }
}
let reason: Notification.RemoveReason = Notification.RemoveReason.CANCEL_REASON_REMOVE;
Notification.remove(hashCode, reason, removeCallback);
```

<!--DelEnd-->


## remove

```TypeScript
function remove(hashCode: string, reason: RemoveReason): Promise<void>
```

Removes a notification for a specified bundle. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [remove](arkts-notification-notificationsubscribe-remove-f-sys.md#remove-5)(hashCode: string, reason: RemoveReason)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function remove(hashCode: string, reason: RemoveReason): Promise<void>--><!--Device-notification-function remove(hashCode: string, reason: RemoveReason): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hashCode | string | Yes | Unique notification ID. |
| reason | RemoveReason | Yes | Reason for notification deletion. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let hashCode: string = 'hashCode';
let reason: Notification.RemoveReason = Notification.RemoveReason.CLICK_REASON_REMOVE;
Notification.remove(hashCode, reason).then(() => {
  console.info("remove success");
}).catch((err: Base.BusinessError) => {
  console.error(`remove failed, code is ${err}`);
});
```

<!--DelEnd-->
