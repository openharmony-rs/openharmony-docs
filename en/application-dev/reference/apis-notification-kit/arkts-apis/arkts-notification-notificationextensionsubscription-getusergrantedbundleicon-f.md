# getUserGrantedBundleIcon

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## getUserGrantedBundleIcon

```TypeScript
function getUserGrantedBundleIcon(bundleName: string): Promise<image.PixelMap>
```

Queries the icons of apps whose switch is turned on in the list of obtained local notifications in this app. This API uses a promise to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.SUBSCRIBE_NOTIFICATION

**Model restriction:** This API can be used only in the stage model.

<!--Device-notificationExtensionSubscription-function getUserGrantedBundleIcon(bundleName: string): Promise<image.PixelMap>--><!--Device-notificationExtensionSubscription-function getUserGrantedBundleIcon(bundleName: string): Promise<image.PixelMap>-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the application icon. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. Possible cause: 1.IPC communication failed. 2.Memory operation error. 3.Failed to obtain or decode the application icon. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600022](../errorcode-notification.md#1600022-invalid-bundle-information) | The specified bundle is invaild. Possible cause: 1.The application is not in the list. 2.The application is disabled. |
