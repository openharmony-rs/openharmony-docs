# getDeviceRemindType (System API)

## Modules to Import

```TypeScript
```

## getDeviceRemindType

```TypeScript
function getDeviceRemindType(callback: AsyncCallback<DeviceRemindType>): void
```

Obtains the notification reminder type. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getDeviceRemindType](arkts-notification-notificationmanager-getdeviceremindtype-f-sys.md#getdeviceremindtype-1)(callback: AsyncCallback&lt;DeviceRemindType&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function getDeviceRemindType(callback: AsyncCallback<DeviceRemindType>): void--><!--Device-notification-function getDeviceRemindType(callback: AsyncCallback<DeviceRemindType>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DeviceRemindType&gt; | Yes | Callback invoked to return the [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode). |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let getDeviceRemindTypeCallback = (err: Base.BusinessError, data: Notification.DeviceRemindType) => {
  if (err) {
    console.error("getDeviceRemindType failed " + JSON.stringify(err));
  } else {
    console.info("getDeviceRemindType success");
  }
};

Notification.getDeviceRemindType(getDeviceRemindTypeCallback);
```

<!--DelEnd-->


## getDeviceRemindType

```TypeScript
function getDeviceRemindType(): Promise<DeviceRemindType>
```

Obtains the notification reminder type. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getDeviceRemindType](arkts-notification-notificationmanager-getdeviceremindtype-f-sys.md)()

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function getDeviceRemindType(): Promise<DeviceRemindType>--><!--Device-notification-function getDeviceRemindType(): Promise<DeviceRemindType>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;DeviceRemindType&gt; | Promise used to return the result of obtaining the [notification reminder mode](../../../notification/notification-glossary.md#notification-reminder-mode). |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

Notification.getDeviceRemindType().then((data: Notification.DeviceRemindType) => {
  console.info("getDeviceRemindType success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`getDeviceRemindType failed, code is ${err}`);
});
```

<!--DelEnd-->
