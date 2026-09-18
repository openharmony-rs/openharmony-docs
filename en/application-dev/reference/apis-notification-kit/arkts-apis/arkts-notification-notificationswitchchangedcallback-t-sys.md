# NotificationSwitchChangedCallback (System API)

```TypeScript
export type NotificationSwitchChangedCallback = (callbackData: NotificationSwitchChangedCallbackData) => void
```

Registers the callback for notification switch state changes set by [notificationManager.setNotificationSwitch] [setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md) API.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackData | [NotificationSwitchChangedCallbackData](arkts-notification-notificationsubscriber-notificationswitchchangedcallbackdata-i-sys.md) | Yes | Callback that returns the notification switch state change information set by [notificationManager.setNotificationSwitch] [setNotificationSwitch](arkts-notification-notificationmanager-setnotificationswitch-f-sys.md) API. |
