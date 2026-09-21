# NotificationSystemLiveViewContent

```TypeScript
export interface NotificationSystemLiveViewContent extends NotificationBasicContent
```

Describes the system live view notification content, which is used to display real-time status information in the live view. Third-party applications are not supported to directly create this notification type. After the system proxy creates a system live view notification, a third-party application can publish a notification with the same ID to update the specified content. This API is inherited from NotificationBasicContent.

> **NOTE:** 
> 
> The actual display effect depends on the device capabilities and the notification center UI style.

**Inheritance/Implementation:** NotificationSystemLiveViewContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## cardButtons

```TypeScript
cardButtons?: Array<NotificationIconButton>
```

Live view buttons (a maximum of three buttons are supported). This parameter is left empty by default.

**Type:** Array&lt;[NotificationIconButton](arkts-notification-notificationcontent-notificationiconbutton-i-sys.md)&gt;

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## liveViewType

```TypeScript
liveViewType?: LiveViewTypes
```

Live view types. The default value is **LIVE_VIEW_ACTIVITY**.

**Type:** [LiveViewTypes](arkts-notification-notificationcontent-liveviewtypes-e-sys.md)

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
