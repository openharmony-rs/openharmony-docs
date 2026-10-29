# enableNotification (System API)

## Modules to Import

```TypeScript
```

## enableNotification

```TypeScript
function enableNotification(bundle: BundleOption, enable: boolean, callback: AsyncCallback<void>): void
```

Sets whether to enable notification for a specified application. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setNotificationEnable](arkts-notification-notificationmanager-setnotificationenable-f-sys.md#setnotificationenable-1)(bundle: BundleOption, enable: boolean, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function enableNotification(bundle: BundleOption, enable: boolean, callback: AsyncCallback<void>): void--><!--Device-notification-function enableNotification(bundle: BundleOption, enable: boolean, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle information of the application. |
| enable | boolean | Yes | Whether to enable notification. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let enableNotificationCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("enableNotification failed " + JSON.stringify(err));
  } else {
    console.info("enableNotification success");
  }
}
let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};
Notification.enableNotification(bundle, false, enableNotificationCallback);
```

<!--DelEnd-->


## enableNotification

```TypeScript
function enableNotification(bundle: BundleOption, enable: boolean): Promise<void>
```

Sets whether to enable notification for a specified application. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setNotificationEnable](arkts-notification-notificationmanager-setnotificationenable-f-sys.md#setnotificationenable-2)(bundle: BundleOption, enable: boolean)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function enableNotification(bundle: BundleOption, enable: boolean): Promise<void>--><!--Device-notification-function enableNotification(bundle: BundleOption, enable: boolean): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle information of the application. |
| enable | boolean | Yes | Whether to enable notification. |

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
Notification.enableNotification(bundle, false).then(() => {
  console.info("enableNotification success");
}).catch((err: Base.BusinessError) => {
  console.error(`enableNotification failed, code is ${err}`);
});
```

<!--DelEnd-->
