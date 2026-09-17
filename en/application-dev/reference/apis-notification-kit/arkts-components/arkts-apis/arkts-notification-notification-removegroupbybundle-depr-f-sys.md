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

**Substitutes:** [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Bundle information of the application. |
| groupName | string | Yes | Name of the notification group. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |


## removeGroupByBundle

```TypeScript
function removeGroupByBundle(bundle: BundleOption, groupName: string): Promise<void>
```

Removes notifications under a notification group of a specified application. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [removeGroupByBundle](arkts-notification-notificationmanager-removegroupbybundle-f-sys.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

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
| Promise&lt;void&gt; | the promise returned by the function. |
