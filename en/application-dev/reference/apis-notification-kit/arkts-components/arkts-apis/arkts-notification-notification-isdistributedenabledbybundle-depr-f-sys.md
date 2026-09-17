# isDistributedEnabledByBundle (System API)

## Modules to Import

```TypeScript
```

## isDistributedEnabledByBundle

```TypeScript
function isDistributedEnabledByBundle(bundle: BundleOption, callback: AsyncCallback<boolean>): void
```

Obtains whether an application supports distributed notifications based on the bundle. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Application bundle. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. |


## isDistributedEnabledByBundle

```TypeScript
function isDistributedEnabledByBundle(bundle: BundleOption): Promise<boolean>
```

Checks whether a specified application supports distributed notifications. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isDistributedEnabledByBundle](arkts-notification-notificationmanager-isdistributedenabledbybundle-f-sys.md)

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | BundleOption | Yes | Application bundle. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. |
