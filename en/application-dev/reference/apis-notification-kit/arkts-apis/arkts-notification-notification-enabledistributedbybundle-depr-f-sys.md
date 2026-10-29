# enableDistributedByBundle (System API)

## Modules to Import

```TypeScript
```

## enableDistributedByBundle

```TypeScript
function enableDistributedByBundle(bundle: BundleOption, enable: boolean, callback: AsyncCallback<void>): void
```

Sets whether the specified application supports [distributed notifications](../../../notification/notification-glossary.md#distributed-notification). This API uses a callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDistributedEnableByBundle](arkts-notification-notificationmanager-setdistributedenablebybundle-f-sys.md#setdistributedenablebybundle-1)(bundle: BundleOption, enable: boolean, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function enableDistributedByBundle(bundle: BundleOption, enable: boolean, callback: AsyncCallback<void>): void--><!--Device-notification-function enableDistributedByBundle(bundle: BundleOption, enable: boolean, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle information of the application. |
| enable | boolean | Yes | Whether the device supports distributed notifications. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let enableDistributedByBundleCallback = (err: Base.BusinessError) => {
  if (err) {
    console.error("enableDistributedByBundle failed " + JSON.stringify(err));
  } else {
    console.info("enableDistributedByBundle success");
  }
};

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};

let enable: boolean = true;

Notification.enableDistributedByBundle(bundle, enable, enableDistributedByBundleCallback);
```

<!--DelEnd-->


## enableDistributedByBundle

```TypeScript
function enableDistributedByBundle(bundle: BundleOption, enable: boolean): Promise<void>
```

Sets whether the specified application supports [distributed notifications](../../../notification/notification-glossary.md#distributed-notification). This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setDistributedEnableByBundle](arkts-notification-notificationmanager-setdistributedenablebybundle-f-sys.md#setdistributedenablebybundle-2)(bundle: BundleOption, enable: boolean)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function enableDistributedByBundle(bundle: BundleOption, enable: boolean): Promise<void>--><!--Device-notification-function enableDistributedByBundle(bundle: BundleOption, enable: boolean): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle of the application. |
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

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};

Notification.enableDistributedByBundle(bundle, enable).then(() => {
  console.info("enableDistributedByBundle success");
}).catch((err: Base.BusinessError) => {
  console.error(`enableDistributedByBundle failed, code is ${err}`);
});
```

<!--DelEnd-->
