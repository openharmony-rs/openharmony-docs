# requestEnableNotification

## Modules to Import

```TypeScript
```

## requestEnableNotification

```TypeScript
function requestEnableNotification(callback: AsyncCallback<void>): void
```

Requests notification to be enabled for this application. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md#requestenablenotification-1)(callback: AsyncCallback&lt;void&gt;)

<!--Device-notification-function requestEnableNotification(callback: AsyncCallback<void>): void--><!--Device-notification-function requestEnableNotification(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';

let requestEnableNotificationCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("requestEnableNotification failed " + JSON.stringify(err));
  } else {
    console.info("requestEnableNotification success");
  }
};

Notification.requestEnableNotification(requestEnableNotificationCallback);
```


## requestEnableNotification

```TypeScript
function requestEnableNotification(): Promise<void>
```

Requests notification to be enabled for this application. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [requestEnableNotification](arkts-notification-notificationmanager-requestenablenotification-f.md)()

<!--Device-notification-function requestEnableNotification(): Promise<void>--><!--Device-notification-function requestEnableNotification(): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import Base from '@ohos.base';

Notification.requestEnableNotification().then(() => {
  console.info("requestEnableNotification success");
}).catch((err: Base.BusinessError) => {
  console.error(`requestEnableNotification failed, code is ${err}`);
});
```
