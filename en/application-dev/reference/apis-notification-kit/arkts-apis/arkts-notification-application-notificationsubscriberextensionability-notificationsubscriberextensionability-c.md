# NotificationSubscriberExtensionAbility

```TypeScript
declare class NotificationSubscriberExtensionAbility
```

NotificationSubscriberExtensionAbility is the base class of the [notification subscription](../../../notification/notification-glossary.md#notification-subscription) extension ability, providing notification subscription related capabilities. Third-party wearable applications (such as companion applications for watches) implement callback logic by inheriting from this class, receive notification information when a notification is published on the local device and forward it to the wearable device over Bluetooth. When a local notification is canceled, they receive the cancellation callback and forward it to the wearable device to delete the corresponding notification.

Use this module when your wearable application needs to obtain local notifications and sync them to a paired wearable device. This module is used together with the **notificationExtensionSubscription** module. This module is responsible for receiving and processing notification data in callbacks, while the **notificationExtensionSubscription** module is responsible for management operations such as authorization, subscription, and unsubscription.

**Since:** 22

<!--Device-unnamed-declare class NotificationSubscriberExtensionAbility--><!--Device-unnamed-declare class NotificationSubscriberExtensionAbility-End-->

**System capability:** SystemCapability.Notification.Notification

## ExtensionAbility Usage Restrictions

To ensure system security and stability, NotificationSubscriberExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { NotificationSubscriberExtensionAbility } from '@kit.NotificationKit';
```

## onCancelMessages

```TypeScript
onCancelMessages(hashCodes: Array<string>): void
```

Called when notifications are canceled.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSubscriberExtensionAbility-onCancelMessages(hashCodes: Array<string>): void--><!--Device-NotificationSubscriberExtensionAbility-onCancelMessages(hashCodes: Array<string>): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hashCodes | Array&lt;string&gt; | Yes | List of hash codes of the notifications to cancel, obtained through [onReceiveMessage](#onreceivemessage). |

**Examples**

```TypeScript
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onCancelMessages(hashCodes: Array<string>): void {
    console.info(`${TAG} onCancelMessages. hashCodes: ${JSON.stringify(hashCodes)}`);
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Triggered when the [notification subscription](../../../notification/notification-glossary.md#notification-subscription) extension is destroyed.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSubscriberExtensionAbility-onDestroy(): void--><!--Device-NotificationSubscriberExtensionAbility-onDestroy(): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Examples**

```TypeScript
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onDestroy(): void {
    console.info(`${TAG} onDestroy`);
  }
}
```

## onReceiveMessage

```TypeScript
onReceiveMessage(notificationInfo: NotificationInfo): void
```

Called when a notification is received.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSubscriberExtensionAbility-onReceiveMessage(notificationInfo: NotificationInfo): void--><!--Device-NotificationSubscriberExtensionAbility-onReceiveMessage(notificationInfo: NotificationInfo): void-End-->

**System capability:** SystemCapability.Notification.Notification

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| notificationInfo | [NotificationInfo](arkts-notification-notificationinfo-i.md) | Yes | Callback information about the notification received in the notification subscription extension ability. |

**Examples**

```TypeScript
const TAG = 'NotificationSubscriberExtAbility';

export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
  onReceiveMessage(notificationInfo: notificationExtensionSubscription.NotificationInfo): void {
    console.info(`${TAG} onReceiveMessage. notificationInfo: ${JSON.stringify(notificationInfo)}`);
  }
}
```

## context

```TypeScript
context: NotificationSubscriberExtensionContext
```

Context for the NotificationSubscriberExtensionAbility.

**Type:** [NotificationSubscriberExtensionContext](arkts-notification-application-notificationsubscriberextensioncontext-notificationsubscriberextensioncontext-c.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationSubscriberExtensionAbility-context: NotificationSubscriberExtensionContext--><!--Device-NotificationSubscriberExtensionAbility-context: NotificationSubscriberExtensionContext-End-->

**System capability:** SystemCapability.Notification.Notification

## Appendix

NotificationSubscriberExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Form Kit | [@ohos.app.form.formBindingData](../../apis-form-kit/arkts-apis/arkts-form-app-form-formbindingdata.md) |
| Form Kit | [@ohos.app.form.formHost](../../apis-form-kit/arkts-apis/arkts-form-app-form-formhost.md) |
| Form Kit | [@ohos.app.form.formInfo](../../apis-form-kit/arkts-apis/arkts-form-app-form-forminfo.md) |
| Form Kit | [@ohos.app.form.formProvider](../../apis-form-kit/arkts-apis/arkts-form-app-form-formprovider.md) |
| Form Kit | [@ohos.app.form.FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability.md) |
| Form Kit | [@ohos.application.formBindingData](../../apis-form-kit/arkts-apis/arkts-form-application-formbindingdata.md) |
| Form Kit | [@ohos.application.formHost](../../apis-form-kit/arkts-apis/arkts-form-application-formhost.md) |
| Form Kit | [@ohos.application.formInfo](../../apis-form-kit/arkts-apis/arkts-form-application-forminfo.md) |
| Form Kit | [@ohos.application.formProvider](../../apis-form-kit/arkts-apis/arkts-form-application-formprovider.md) |
| Notification Kit | [@ohos.notification](../../apis-notification-kit/arkts-apis/arkts-notification-notification.md) |
| Notification Kit | [@ohos.notificationManager](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager.md) |
| ArkUI | [@ohos.prompt](../../apis-arkui/arkts-apis/arkts-arkui-prompt.md) |
| ArkUI | [@ohos.promptAction](../../apis-arkui/arkts-apis/arkts-arkui-promptaction.md) |
| Telephony Kit | [telephony.voipCall](../../apis-telephony-kit/arkts-apis/arkts-telephony-voipcall.md) |
| ArkUI | [@ohos.window](../../apis-arkui/arkts-apis/arkts-arkui-window.md) |
