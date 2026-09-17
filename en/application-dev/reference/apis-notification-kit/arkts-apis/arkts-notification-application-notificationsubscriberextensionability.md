# @ohos.application.NotificationSubscriberExtensionAbility

## Modules to Import

```TypeScript
import { NotificationSubscriberExtensionAbility } from '@kit.NotificationKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [NotificationSubscriberExtensionAbility](arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md) | NotificationSubscriberExtensionAbility is the base class for notification subscriber extension abilities, providing notification subscription-related functionality. Third-party wearable apps (such as companion applications for watches)implement callback logic by inheriting this class, receiving notification information when notifications are published on the local device and forwarding them to the wearable device via Bluetooth, and receiving callbacks for notification cancellation when local notifications are cancelled and forwarding them to the wearable device to delete the corresponding notifications. |
