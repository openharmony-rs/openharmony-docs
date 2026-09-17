# openSubscriptionSettingsWithResult

## Modules to Import

```TypeScript
import { notificationExtensionSubscription } from '@kit.NotificationKit';
```

## openSubscriptionSettingsWithResult

```TypeScript
function openSubscriptionSettingsWithResult(context: UIAbilityContext): Promise<UserGrantSetting>
```

Opens the settings screen of notification extension subscription in a semi-modal dialog box. On this screen, the user can toggle on the **Allow access to notifications on this device** switch and grant access to notifications for specified applications. This API uses a promise to return the result. When the semi-modal window is closed, the user-defined authorization result is returned.

**Since:** 26.0.0

**Required permissions:** ohos.permission.SUBSCRIBE_NOTIFICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | Yes | Ability context bound to the notification settings page. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[UserGrantSetting](arkts-notification-notificationextensionsubscription-usergrantsetting-t.md)&gt; | Promise used to return the result of the authorization set by the user. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied or current device not supported. |
| [1600001](../errorcode-notification.md#1600001-internal-error) | Internal error. |
| [1600018](../errorcode-notification.md#1600018-notification-settings-page-already-displayed) | The notification settings window is already displayed. |
| [1600023](../errorcode-notification.md#1600023-notificationsubscriberextensionability-not-implemented) | The application does not implement the NotificationSubscriberExtensionAbility. |

**Examples**

```TypeScript
import { common } from '@kit.AbilityKit';

try {
  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  notificationExtensionSubscription.openSubscriptionSettingsWithResult(context).then((data) => {
    console.info(`openSubscriptionSettingsWithResult success, data: ${JSON.stringify(data)}`);
  }).catch((e: Error) => {
    let error = e as BusinessError
    console.error(`failed to call openSubscriptionSettingsWithResult, code is ${error.code}, message is ${error.message}`)
  });
} catch (error) {
  console.error(`failed to call openSubscriptionSettingsWithResult, code is ${error.code}, message is ${error.message}`)
}
```
