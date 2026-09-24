# getUserGrantedEnabledBundles

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

<a id="getusergrantedenabledbundles-1"></a>

## getUserGrantedEnabledBundles

```TypeScript
function getUserGrantedEnabledBundles(): Promise<GrantedBundleInfo[]>
```

Obtains the applications that are allowed to access device notifications for the current application. This API uses a promise to return the result.

**Since:** 22

**Required permissions:** ohos.permission.SUBSCRIBE_NOTIFICATION

**System capability:** SystemCapability.Notification.Notification

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[GrantedBundleInfo](arkts-notification-notificationextensionsubscription-grantedbundleinfo-t.md)[]&gt; | Promise used to return the list of applications that are allowed to access device notifications for the current application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied or current device not supported. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |

**Examples**

```TypeScript
notificationExtensionSubscription.getUserGrantedEnabledBundles().then((data: notificationExtensionSubscription.GrantedBundleInfo[]) => {
  console.info(`getUserGrantedEnabledBundles successfully. Data: ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`getUserGrantedEnabledBundles fail, code is ${err.code}, message is ${err.message}`);
});
```
