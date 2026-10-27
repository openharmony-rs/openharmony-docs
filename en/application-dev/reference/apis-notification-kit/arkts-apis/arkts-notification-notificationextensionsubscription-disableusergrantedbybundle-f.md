# disableUserGrantedByBundle

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## disableUserGrantedByBundle

```TypeScript
function disableUserGrantedByBundle(bundle: GrantedBundleInfo): Promise<void>
```

Disables the switch status of a specified app in the list of obtained local notifications in this app. This API uses a promise to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.SUBSCRIBE_NOTIFICATION

**Model restriction:** This API can be used only in the stage model.

<!--Device-notificationExtensionSubscription-function disableUserGrantedByBundle(bundle: GrantedBundleInfo): Promise<void>--><!--Device-notificationExtensionSubscription-function disableUserGrantedByBundle(bundle: GrantedBundleInfo): Promise<void>-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundle | [GrantedBundleInfo](arkts-notification-notificationextensionsubscription-grantedbundleinfo-t.md) | Yes | Describes the bundle information of the authorized application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. 3.Database operation failed. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600022](../errorcode-notification.md#1600022-invalid-bundle-information) | The specified bundle is invaild. |
