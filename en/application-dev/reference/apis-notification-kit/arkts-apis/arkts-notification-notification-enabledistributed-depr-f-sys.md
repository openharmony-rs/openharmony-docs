# enableDistributed (System API)

## Modules to Import

```TypeScript
```

## enableDistributed

```TypeScript
function enableDistributed(enable: boolean, callback: AsyncCallback<void>): void
```

Sets whether the device supports [distributed notifications](../../../notification/notification-glossary.md#distributed-notification). This API uses a callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDistributedEnable](arkts-notification-notificationmanager-setdistributedenable-f-sys.md#setdistributedenable-1)(enable: boolean, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function enableDistributed(enable: boolean, callback: AsyncCallback<void>): void--><!--Device-notification-function enableDistributed(enable: boolean, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether the device supports distributed notifications. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let enabledNotificationCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("enableDistributed failed " + JSON.stringify(err));
  } else {
    console.info("enableDistributed success");
  }
};

let enable: boolean = true;

Notification.enableDistributed(enable, enabledNotificationCallback);
```

<!--DelEnd-->


## enableDistributed

```TypeScript
function enableDistributed(enable: boolean): Promise<void>
```

Sets whether the device supports [distributed notifications](../../../notification/notification-glossary.md#distributed-notification). This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDistributedEnable](arkts-notification-notificationmanager-setdistributedenable-f-sys.md#setdistributedenable-2)(enable: boolean)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function enableDistributed(enable: boolean): Promise<void>--><!--Device-notification-function enableDistributed(enable: boolean): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether the device supports distributed notifications. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let enable: boolean = true;
Notification.enableDistributed(enable).then(() => {
  console.info("enableDistributed success");
}).catch((err: Base.BusinessError) => {
  console.error(`enableDistributed failed, code is ${err}`);
});
```

<!--DelEnd-->
