# NotificationMultiLineContent

Describes the multi-line text notification. This API is inherited from NotificationBasicContent.

> **NOTE:** 
> 
> - When this notification type forms a group notification with other notifications, its display effect defaults to the collapsed state, and the displayed title and body are the **title** and **text** inherited from NotificationBasicContent. When this notification type is displayed alone and does not form a group notification with other notifications, its display effect defaults to the expanded state, where the displayed title is the expanded title **longTitle**, and the multi-line text content **lines** is displayed as the body.
> 
> - When a user taps a group notification to view the notification details, the display effect of this notification changes to the expanded state.
> 
> - The actual display effect depends on the device capabilities and the notification center UI style.

**Inheritance/Implementation:** NotificationMultiLineContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## lineWantAgents

```TypeScript
lineWantAgents?: Array<WantAgent>
```

**wantAgent**s triggered when a line of text in the multi-line text is tapped. The text in different lines corresponds to different **wantAgent**s. The maximum number of lines configured for this field is equal to the value of lines. This parameter is left empty by default.

**Type:** Array&lt;[WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md)&gt;

**Since:** 20

**Required permissions:** ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
