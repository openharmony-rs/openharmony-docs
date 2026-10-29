# NotificationContent (System API)

```TypeScript
export interface NotificationContent
```

NotificationContent defines the content structure of a notification and provides interfaces for describing multiple notification content types. When an application needs to publish a notification, it can select the corresponding content type interface to construct the [notification content](../../../notification/notification-glossary.md#notification-content) based on the display requirements of the notification (such as basic text, long text, multi-line text, picture, and live view).

**Since:** 7

<!--Device-unnamed-export interface NotificationContent--><!--Device-unnamed-export interface NotificationContent-End-->

**System capability:** SystemCapability.Notification.Notification

## liveView

```TypeScript
liveView?: NotificationLiveViewContent
```

Normal live view type [notification content](../../../notification/notification-glossary.md#notification-content).

**Type:** [NotificationLiveViewContent](arkts-notification-notificationcontent-notificationliveviewcontent-i-sys.md)

**Since:** 11

<!--Device-NotificationContent-liveView?: NotificationLiveViewContent--><!--Device-NotificationContent-liveView?: NotificationLiveViewContent-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
