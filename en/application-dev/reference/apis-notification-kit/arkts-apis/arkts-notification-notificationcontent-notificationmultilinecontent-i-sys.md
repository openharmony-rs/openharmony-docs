# NotificationMultiLineContent (System API)

```TypeScript
export interface NotificationMultiLineContent extends NotificationBasicContent
```

Describes the multi-line text notification. This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md).

> **NOTE:** 
> 
> - When this type of notification forms a [group notification](../../../notification/notification-glossary.md#group-notification) with other notifications,the display effect of this notification type defaults to the collapsed state, and the displayed title and body are the `title` and `text` of the [basic text](arkts-notification-notificationcontent-notificationbasiccontent-i.md) inherited by this type.

When this type of notification is displayed individually and does not form a group notification with other notifications, the display effect of this notification type defaults to the expanded state, the displayed title is the expanded title `longTitle`, and the multi-line text content `lines` is displayed as the body in multiple lines.

> - When the user clicks a notification in grouped display to view each notification's details, the display effect of this notification changes to the expanded state.
> 
> - The actual display effect depends on the device capability and the [notification center](../../../notification/notification-glossary.md#notification-center) UI style.

**Inheritance/Implementation:** NotificationMultiLineContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**Since:** 7

<!--Device-unnamed-export interface NotificationMultiLineContent extends NotificationBasicContent--><!--Device-unnamed-export interface NotificationMultiLineContent extends NotificationBasicContent-End-->

**System capability:** SystemCapability.Notification.Notification

## lineWantAgents

```TypeScript
lineWantAgents?: Array<WantAgent>
```

**wantAgent**s triggered when a line of text in the multi-line text is tapped. The text in different lines corresponds to different **wantAgent**s. The number of lines configured for this field cannot be greater than the number of [lines](arkts-notification-notificationcontent-notificationmultilinecontent-i.md). This parameter is left empty by default.

ohos.permission.NOTIFICATION_AGENT_CONTROLLER

**Type:** Array&lt;[WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md)&gt;

**Since:** 20

**Required permissions:** ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationMultiLineContent-lineWantAgents?: Array<WantAgent>--><!--Device-NotificationMultiLineContent-lineWantAgents?: Array<WantAgent>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
