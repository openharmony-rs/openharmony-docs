# isDistributedEnabled

## Modules to Import

```TypeScript
```

## isDistributedEnabled

```TypeScript
function isDistributedEnabled(callback: AsyncCallback<boolean>): void
```

Checks whether the device supports [distributed notification](../../../notification/notification-glossary.md#distributed-notification). This API uses a callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md#isdistributedenabled-1)(callback: AsyncCallback&lt;boolean&gt;)

<!--Device-notification-function isDistributedEnabled(callback: AsyncCallback<boolean>): void--><!--Device-notification-function isDistributedEnabled(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';

let isDistributedEnabledCallback = (err: Base.BusinessError, data: boolean) => {
  if (err) {
    console.error("isDistributedEnabled failed " + JSON.stringify(err));
  } else {
    console.info("isDistributedEnabled success " + JSON.stringify(data));
  }
};

Notification.isDistributedEnabled(isDistributedEnabledCallback);
```


## isDistributedEnabled

```TypeScript
function isDistributedEnabled(): Promise<boolean>
```

Checks whether the device supports [distributed notification](../../../notification/notification-glossary.md#distributed-notification). This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isDistributedEnabled](arkts-notification-notificationmanager-isdistributedenabled-f.md)()

<!--Device-notification-function isDistributedEnabled(): Promise<boolean>--><!--Device-notification-function isDistributedEnabled(): Promise<boolean>-End-->

**System capability:** SystemCapability.Notification.Notification

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import Base from '@ohos.base';

Notification.isDistributedEnabled().then((data: boolean) => {
    console.info("isDistributedEnabled success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`isDistributedEnabled failed, code is ${err}`);
});
```
