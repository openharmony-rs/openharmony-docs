# @ohos.application.NotificationSubscriberExtensionAbility(ExtensionAbility for Notification Subscription)

## Modules to Import

```TypeScript
import { NotificationSubscriberExtensionAbility } from '@kit.NotificationKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [NotificationSubscriberExtensionAbility](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md) | NotificationSubscriberExtensionAbility is the base class of the [notification subscription](../../../notification/notification-glossary.md#notification-subscription) extension ability, providing notification subscription related capabilities. Third-party wearable applications (such as companion applications for watches) implement callback logic by inheriting from this class, receive notification information when a notification is published on the local device and forward it to the wearable device over Bluetooth. When a local notification is canceled, they receive the cancellation callback and forward it to the wearable device to delete the corresponding notification. |
