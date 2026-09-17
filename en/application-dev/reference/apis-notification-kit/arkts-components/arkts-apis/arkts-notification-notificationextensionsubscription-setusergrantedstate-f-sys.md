# setUserGrantedState (System API)

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## setUserGrantedState

```TypeScript
function setUserGrantedState(targetBundle: BundleOption, enabled: boolean): Promise<void>
```

Sets the enabling state of the **Allow access to notifications on this device** switch for a specified application. This API uses a promise to return the result.

**Since:** 22

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetBundle | [BundleOption](arkts-notification-notificationextensionsubscription-bundleoption-t.md) | Yes | Information about the target application. The application must have requested the ohos.permission.SUBSCRIBE_NOTIFICATION permission and implemented [NotificationSubscriberExtensionAbility](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md). Otherwise, error code 1600022 is returned. |
| enabled | boolean | Yes | Whether to enable the device notification access. The value **true** indicates that this functionality is enabled, and **false** indicates the opposite. |

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
| [1600003](../errorcode-notification.md#1600003-failed-to-connect-to-the-notification-service) | Failed to connect to the service. |
| [1600022](../errorcode-notification.md#1600022-invalid-bundle-information) | The specified bundle is invalid. |

**Examples**

```TypeScript
let targetBundle: notificationExtensionSubscription.BundleOption =
{
  // Use the actual target application information.
  bundle: 'com.example.testnotification',
};
notificationExtensionSubscription.setUserGrantedState(targetBundle, true).then(() => {
  console.info(`setUserGrantedState successfully.`);
}).catch((err: BusinessError) => {
  console.error(`setUserGrantedState fail, code is ${err.code}, message is ${err.message}`);
});
```
