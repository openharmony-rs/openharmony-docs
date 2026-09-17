# setBadgeDisplayStatusByBundles (System API)

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## setBadgeDisplayStatusByBundles

```TypeScript
function setBadgeDisplayStatusByBundles(badges: Map<BundleOption, boolean>) : Promise<void>
```

Batch sets whether to display badges for specified applications. This API uses a promise to return the result.

**Since:** 21

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| badges | Map&lt;[BundleOption](arkts-notification-notificationmanager-bundleoption-t.md), boolean&gt; | Yes | List containing bundle names and badge display statuses. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application to call the interface. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-marshalling-or-unmarshalling-error) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-insufficient-memory-space) | No memory space. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let badges = new Map<notificationManager.BundleOption, boolean>();
let bundle: notificationManager.BundleOption = {
    bundle: 'bundleName',
};
badges.set(bundle, true);

notificationManager.setBadgeDisplayStatusByBundles(badges).then(() => {
    console.info('SetBadgeDisplayStatusByBundles success.');
}).catch((err: BusinessError) => {
    console.error(`SetBadgeDisplayStatusByBundles failed, code is ${err.code}, message is ${err.message}`);
});
```
