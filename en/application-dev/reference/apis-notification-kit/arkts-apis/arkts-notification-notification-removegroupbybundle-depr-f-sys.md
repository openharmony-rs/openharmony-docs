# removeGroupByBundle (System API)

## Modules to Import

```TypeScript
```

## removeGroupByBundle

```TypeScript
function removeGroupByBundle(bundle: BundleOption, groupName: string, callback: AsyncCallback<void>): void
```

Removes notifications under a notification group of a specified application. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md#removegroupbybundle-1)(bundle: BundleOption, groupName: string, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function removeGroupByBundle(bundle: BundleOption, groupName: string, callback: AsyncCallback<void>): void--><!--Device-notification-function removeGroupByBundle(bundle: BundleOption, groupName: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle information of the application. |
| groupName | string | Yes | Name of the notification group. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let removeGroupByBundleCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("removeGroupByBundle failed " + JSON.stringify(err));
  } else {
    console.info("removeGroupByBundle success");
  }
}

let bundleOption: Notification.BundleOption = {bundle: "Bundle"};
let groupName: string = "GroupName";

Notification.removeGroupByBundle(bundleOption, groupName, removeGroupByBundleCallback);
```

<!--DelEnd-->


## removeGroupByBundle

```TypeScript
function removeGroupByBundle(bundle: BundleOption, groupName: string): Promise<void>
```

Removes notifications under a notification group of a specified application. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md#removegroupbybundle-2)(bundle: BundleOption, groupName: string)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function removeGroupByBundle(bundle: BundleOption, groupName: string): Promise<void>--><!--Device-notification-function removeGroupByBundle(bundle: BundleOption, groupName: string): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle information of the application. |
| groupName | string | Yes | Name of the notification group. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let bundleOption: Notification.BundleOption = {bundle: "Bundle"};
let groupName: string = "GroupName";
Notification.removeGroupByBundle(bundleOption, groupName).then(() => {
  console.info("removeGroupByBundle success");
}).catch((err: Base.BusinessError) => {
  console.error(`removeGroupByBundle failed, code is ${err}`);
});
```

<!--DelEnd-->
