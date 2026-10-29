# isDistributedEnabledByBundle (System API)

## Modules to Import

```TypeScript
```

## isDistributedEnabledByBundle

```TypeScript
function isDistributedEnabledByBundle(bundle: BundleOption, callback: AsyncCallback<boolean>): void
```

Obtains whether the application supports [distributed notifications](../../../notification/notification-glossary.md#distributed-notification) based on the application's bundle. This API uses a callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle-1)(bundle: BundleOption, callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function isDistributedEnabledByBundle(bundle: BundleOption, callback: AsyncCallback<boolean>): void--><!--Device-notification-function isDistributedEnabledByBundle(bundle: BundleOption, callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle of the application. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let isDistributedEnabledByBundleCallback = (err: Base.BusinessError, data: boolean) => {
  if (err) {
    console.error("isDistributedEnabledByBundle failed " + JSON.stringify(err));
  } else {
    console.info("isDistributedEnabledByBundle success" + JSON.stringify(data));
  }
};

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};

Notification.isDistributedEnabledByBundle(bundle, isDistributedEnabledByBundleCallback);
```

<!--DelEnd-->


## isDistributedEnabledByBundle

```TypeScript
function isDistributedEnabledByBundle(bundle: BundleOption): Promise<boolean>
```

Queries whether the specified application supports [distributed notifications](../../../notification/notification-glossary.md#distributed-notification). This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md#isdistributedenabledbybundle-2)(bundle: BundleOption)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notification-function isDistributedEnabledByBundle(bundle: BundleOption): Promise<boolean>--><!--Device-notification-function isDistributedEnabledByBundle(bundle: BundleOption): Promise<boolean>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. |

<!--Del-->
**Examples**

```TypeScript
import Base from '@ohos.base';

let bundle: Notification.BundleOption = {
  bundle: "bundleName1",
};

Notification.isDistributedEnabledByBundle(bundle).then((data: boolean) => {
  console.info("isDistributedEnabledByBundle success, data: " + JSON.stringify(data));
}).catch((err: Base.BusinessError) => {
  console.error(`isDistributedEnabledByBundle failed, code is ${err}`);
});
```

<!--DelEnd-->
