# cancelGroup

## Modules to Import

```TypeScript
```

## cancelGroup

```TypeScript
function cancelGroup(groupName: string, callback: AsyncCallback<void>): void
```

Cancels notifications under a notification group of this application. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md#cancelgroup-1)(groupName: string, callback: AsyncCallback&lt;void&gt;)

<!--Device-notification-function cancelGroup(groupName: string, callback: AsyncCallback<void>): void--><!--Device-notification-function cancelGroup(groupName: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| groupName | string | Yes | Name of the notification group, which is specified through [NotificationRequest](arkts-notification-notificationrequest-i.md) when the notification is published. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';

let cancelGroupCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("cancelGroup failed " + JSON.stringify(err));
  } else {
    console.info("cancelGroup success");
  }
}

let groupName: string = "GroupName";

Notification.cancelGroup(groupName, cancelGroupCallback);
```


## cancelGroup

```TypeScript
function cancelGroup(groupName: string): Promise<void>
```

Cancels notifications under a notification group of this application. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [cancelGroup](arkts-notification-notificationmanager-cancelgroup-f.md#cancelgroup-2)(groupName: string)

<!--Device-notification-function cancelGroup(groupName: string): Promise<void>--><!--Device-notification-function cancelGroup(groupName: string): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| groupName | string | Yes | Name of the notification group. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import Base from '@ohos.base';

let groupName: string = "GroupName";
Notification.cancelGroup(groupName).then(() => {
  console.info("cancelGroup success");
}).catch((err: Base.BusinessError) => {
  console.error(`cancelGroup failed, code is ${err}`);
});
```
