# cancel

## Modules to Import

```TypeScript
```

## cancel

```TypeScript
function cancel(id: number, callback: AsyncCallback<void>): void
```

Cancels a notification with the specified ID. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [cancel](arkts-notification-notificationmanager-cancel-f.md)(id: number, callback: AsyncCallback&lt;void&gt;)

<!--Device-notification-function cancel(id: number, callback: AsyncCallback<void>): void--><!--Device-notification-function cancel(id: number, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Notification ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';

// cancel callback
let cancelCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("cancel failed " + JSON.stringify(err));
  } else {
    console.info("cancel success");
  }
}
Notification.cancel(0, cancelCallback);
```


## cancel

```TypeScript
function cancel(id: number, label: string, callback: AsyncCallback<void>): void
```

Cancels a notification with the specified ID and label. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [cancel](arkts-notification-notificationmanager-cancel-f.md)(id: number, label: string, callback: AsyncCallback&lt;void&gt;)

<!--Device-notification-function cancel(id: number, label: string, callback: AsyncCallback<void>): void--><!--Device-notification-function cancel(id: number, label: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Notification ID. |
| label | string | Yes | Notification label. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';

// cancel callback
let cancelCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("cancel failed " + JSON.stringify(err));
  } else {
    console.info("cancel success");
  }
}
Notification.cancel(0, "label", cancelCallback);
```


## cancel

```TypeScript
function cancel(id: number, label?: string): Promise<void>
```

Cancels a notification with the specified ID and optional label. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [cancel](arkts-notification-notificationmanager-cancel-f.md)(id: number, label?: string)

<!--Device-notification-function cancel(id: number, label?: string): Promise<void>--><!--Device-notification-function cancel(id: number, label?: string): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Notification ID. |
| label | string | No | Notification label. This parameter is left empty by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import Base from '@ohos.base';

Notification.cancel(0).then(() => {
  console.info("cancel success");
}).catch((err: Base.BusinessError) => {
  console.error(`cancel failed, code is ${err}`);
});
```
