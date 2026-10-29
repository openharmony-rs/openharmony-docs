# NotificationRequest

```TypeScript
export interface NotificationRequest
```

Defines the data structure of a [notification request](../../../notification/notification-glossary.md#notification-request), which is used to describe all information of a notification, including [notification content](../../../notification/notification-glossary.md#notification-content), identifier, display style, interaction behavior, and so on.

**Since:** 7

<!--Device-unnamed-export interface NotificationRequest--><!--Device-unnamed-export interface NotificationRequest-End-->

**System capability:** SystemCapability.Notification.Notification

## actionButtons

```TypeScript
actionButtons?: Array<NotificationActionButton>
```

[Notification buttons](../../../notification/notification-glossary.md#notification-button). The value is empty by default. A notification can contain at most two buttons. Since API version 16, a notification on a `wearable` device can contain at most three buttons.

**Type:** Array&lt;[NotificationActionButton](arkts-notification-notificationactionbutton-i.md)&gt;

**Since:** 7

<!--Device-NotificationRequest-actionButtons?: Array<NotificationActionButton>--><!--Device-NotificationRequest-actionButtons?: Array<NotificationActionButton>-End-->

**System capability:** SystemCapability.Notification.Notification

## appMessageId

```TypeScript
appMessageId?: string
```

Unique identifier field carried when an application sends a notification. It is used for notification deduplication. If the same application publishes notifications carrying the same **appMessageId** through different slots such as local and cloud, the device displays only one message, and subsequent duplicate notifications received will be silently deduplicated without being displayed or alerted. The deduplication identifier is valid only within 24 hours after the notification is published, and becomes invalid after 24 hours or after the device restarts.

The size does not exceed 202 bytes, and the excess part will be truncated. The value is empty by default.

**Type:** string

**Since:** 12

<!--Device-NotificationRequest-appMessageId?: string--><!--Device-NotificationRequest-appMessageId?: string-End-->

**System capability:** SystemCapability.Notification.Notification

## autoDeletedTime

```TypeScript
autoDeletedTime?: number
```

Scheduled auto-delete time for the notification. You can set this parameter to automatically delete the notification after the specified time. Default value: **0**. This parameter does not take effect if a value less than 0 or a past time is passed in.

Data format: timestamp.

Unit: millisecond.

For example, to delete a notification after it has been retained for 3 seconds (3000 ms), the corresponding deletion time is: **new Date().getTime()** + 3000.

**Type:** number

**Since:** 7

<!--Device-NotificationRequest-autoDeletedTime?: long--><!--Device-NotificationRequest-autoDeletedTime?: long-End-->

**System capability:** SystemCapability.Notification.Notification

## badgeIconStyle

```TypeScript
badgeIconStyle?: number
```

Notification badge type. Not supported currently.

**Type:** number

**Since:** 7

<!--Device-NotificationRequest-badgeIconStyle?: int--><!--Device-NotificationRequest-badgeIconStyle?: int-End-->

**System capability:** SystemCapability.Notification.Notification

## badgeNumber

```TypeScript
badgeNumber?: number
```

Number of notifications displayed on the application icon. The number is displayed cumulatively. The default value is 0.

When the value of `badgeNumber` is less than or equal to 0, this badge setting is ignored.

When the cumulative badge number is greater than 99, the [notification badge](../../../notification/notification-glossary.md#notification-badge) displays 99+.

For example, if the application publishes three notifications and sets `badgeNumber` to 2, 0, and 3 in sequence, the application displays 2, 2, and 5 in sequence.

**Type:** number

**Since:** 9

<!--Device-NotificationRequest-badgeNumber?: long--><!--Device-NotificationRequest-badgeNumber?: long-End-->

**System capability:** SystemCapability.Notification.Notification

## color

```TypeScript
color?: number
```

Background color of the notification. Not supported currently.

**Type:** number

**Since:** 7

<!--Device-NotificationRequest-color?: long--><!--Device-NotificationRequest-color?: long-End-->

**System capability:** SystemCapability.Notification.Notification

## colorEnabled

```TypeScript
colorEnabled?: boolean
```

Whether the notification background color can be enabled. Not supported currently.

**Type:** boolean

**Since:** 7

<!--Device-NotificationRequest-colorEnabled?: boolean--><!--Device-NotificationRequest-colorEnabled?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## content

```TypeScript
content: NotificationContent
```

Notification display content, including the notification title and body.

**Type:** [NotificationContent](arkts-notification-notificationcontent-i.md)

**Since:** 7

<!--Device-NotificationRequest-content: NotificationContent--><!--Device-NotificationRequest-content: NotificationContent-End-->

**System capability:** SystemCapability.Notification.Notification

## creatorBundleName

```TypeScript
readonly creatorBundleName?: string
```

Bundle name of the application that creates the notification.

**Type:** string

**Since:** 7

<!--Device-NotificationRequest-readonly creatorBundleName?: string--><!--Device-NotificationRequest-readonly creatorBundleName?: string-End-->

**System capability:** SystemCapability.Notification.Notification

## creatorPid

```TypeScript
readonly creatorPid?: number
```

PID used for creating the notification.

**Type:** number

**Since:** 7

<!--Device-NotificationRequest-readonly creatorPid?: int--><!--Device-NotificationRequest-readonly creatorPid?: int-End-->

**System capability:** SystemCapability.Notification.Notification

## creatorUid

```TypeScript
readonly creatorUid?: number
```

UID of the application that creates the notification.

**Type:** number

**Since:** 7

<!--Device-NotificationRequest-readonly creatorUid?: int--><!--Device-NotificationRequest-readonly creatorUid?: int-End-->

**System capability:** SystemCapability.Notification.Notification

## creatorUserId

```TypeScript
readonly creatorUserId?: number
```

ID of the user who creates the notification.

**Type:** number

**Since:** 8

<!--Device-NotificationRequest-readonly creatorUserId?: int--><!--Device-NotificationRequest-readonly creatorUserId?: int-End-->

**System capability:** SystemCapability.Notification.Notification

## deliveryTime

```TypeScript
deliveryTime?: number
```

Notification delivery time. This parameter is automatically generated by the system and does not require configuration.

Data format: timestamp.

Unit: millisecond.

**Type:** number

**Since:** 7

<!--Device-NotificationRequest-deliveryTime?: long--><!--Device-NotificationRequest-deliveryTime?: long-End-->

**System capability:** SystemCapability.Notification.Notification

## distributedOption

```TypeScript
distributedOption?: DistributedOptions
```

Options of the [distributed notification](../../../notification/notification-glossary.md#distributed-notification). Not supported currently.

**Type:** [DistributedOptions](arkts-notification-notificationrequest-distributedoptions-i.md)

**Since:** 8

<!--Device-NotificationRequest-distributedOption?: DistributedOptions--><!--Device-NotificationRequest-distributedOption?: DistributedOptions-End-->

**System capability:** SystemCapability.Notification.Notification

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

Extended parameters, used to provide custom services for applications. This parameter is left blank by default.

The key value is assigned by the system. Manual modification does not take effect. The system automatically changes the value to the actual value during data transmission.

- 'ohos.notificationManager.wantUri': uri field in the [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) object, which is  
passed to the application when the user taps a notification. This field can be obtained via the [getActiveNotifications](arkts-notification-notificationmanager-getactivenotifications-f.md) API call.

**Type:** { [key: string]: any }

**Since:** 7

<!--Device-NotificationRequest-extraInfo?: { [key: string]: any }--><!--Device-NotificationRequest-extraInfo?: { [key: string]: any }-End-->

**System capability:** SystemCapability.Notification.Notification

## groupName

```TypeScript
groupName?: string
```

Group to which the notification belongs. When different notifications have the same **groupName**, these notifications will be displayed as a group.

The size does not exceed 202 bytes, and the excess part will be truncated. The value is empty by default.

**Type:** string

**Since:** 8

<!--Device-NotificationRequest-groupName?: string--><!--Device-NotificationRequest-groupName?: string-End-->

**System capability:** SystemCapability.Notification.Notification

## hashCode

```TypeScript
readonly hashCode?: string
```

Unique ID of the notification.

**Type:** string

**Since:** 7

<!--Device-NotificationRequest-readonly hashCode?: string--><!--Device-NotificationRequest-readonly hashCode?: string-End-->

**System capability:** SystemCapability.Notification.Notification

## id

```TypeScript
id?: number
```

Notification ID. The default value is **0**. If a notification with the same ID exists, the notification is updated. If no notification with the same ID exists, a new notification is created.

**Type:** number

**Since:** 7

<!--Device-NotificationRequest-id?: int--><!--Device-NotificationRequest-id?: int-End-->

**System capability:** SystemCapability.Notification.Notification

## isAlertOnce

```TypeScript
isAlertOnce?: boolean
```

Whether to send a notification only once when the notification is published or updated. The default value is **false**.

- **true**: A notification is sent only when the notification is published for the first time. For subsequent  
update, the notification mode is changed to [LEVEL_LOW](arkts-notification-notificationmanager-slotlevel-e.md).  
- **false**: A notification is sent based on the configured notification mode.

**Type:** boolean

**Since:** 7

<!--Device-NotificationRequest-isAlertOnce?: boolean--><!--Device-NotificationRequest-isAlertOnce?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## isCountDown

```TypeScript
isCountDown?: boolean
```

Whether to display the countdown time. Not supported currently.

**Type:** boolean

**Since:** 7

<!--Device-NotificationRequest-isCountDown?: boolean--><!--Device-NotificationRequest-isCountDown?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## isFloatingIcon

```TypeScript
isFloatingIcon?: boolean
```

Whether the notification is displayed as a floating icon in the status bar. Not supported currently.

**Type:** boolean

**Since:** 7

<!--Device-NotificationRequest-isFloatingIcon?: boolean--><!--Device-NotificationRequest-isFloatingIcon?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## isOngoing

```TypeScript
isOngoing?: boolean
```

Not supported currently.

**Type:** boolean

**Since:** 7

<!--Device-NotificationRequest-isOngoing?: boolean--><!--Device-NotificationRequest-isOngoing?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## isStopwatch

```TypeScript
isStopwatch?: boolean
```

Whether to display the stopwatch. Not supported currently.

**Type:** boolean

**Since:** 7

<!--Device-NotificationRequest-isStopwatch?: boolean--><!--Device-NotificationRequest-isStopwatch?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## isUnremovable

```TypeScript
isUnremovable?: boolean
```

Not supported currently.

**Type:** boolean

**Since:** 7

<!--Device-NotificationRequest-isUnremovable?: boolean--><!--Device-NotificationRequest-isUnremovable?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## label

```TypeScript
label?: string
```

Notification label.

The **label** field functions similarly to an ID and can be used alone or combined with the ID to serve as the notification identifier. It is recommended to use the ID.

If the **label** is not empty when a notification is published, the corresponding **label** must also be specified when the notification is updated or deleted.

The size does not exceed 202 bytes, and the excess part will be truncated. The value is empty by default.

**Type:** string

**Since:** 7

<!--Device-NotificationRequest-label?: string--><!--Device-NotificationRequest-label?: string-End-->

**System capability:** SystemCapability.Notification.Notification

## largeIcon

```TypeScript
largeIcon?: image.PixelMap
```

Icon on the right of the notification. The value is empty by default. When `content` uses [NotificationPictureContent](arkts-notification-notificationcontent-notificationpicturecontent-i.md), setting this parameter does not take effect.

The total number of bytes of the icon pixels does not exceed 192KB (the total number of bytes of the icon pixels is obtained through [getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber)). If this limit is exceeded, the setting does not take effect. The recommended icon pixel dimensions are 128*128. The actual display effect depends on device capabilities and the notification center UI style<!--RP1--><!--RP1End-->.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 7

<!--Device-NotificationRequest-largeIcon?: image.PixelMap--><!--Device-NotificationRequest-largeIcon?: image.PixelMap-End-->

**System capability:** SystemCapability.Notification.Notification

## notificationFlags

```TypeScript
notificationFlags?: NotificationFlags
```

[Notification flag](../../../notification/notification-glossary.md#notification-flags) settings. The value is empty by default. This parameter becomes writable since API version 23. Setting this parameter can reduce the notification reminder modes. When the notification slot type is [LIVE_VIEW](arkts-notification-notificationmanager-slottype-e.md), setting this parameter does not take effect.

**Type:** [NotificationFlags](arkts-notification-notificationflags-i.md)

**Since:** 8

**Model restriction:** 
- API version 23 and later: This API can be used in both the stage model and FA model.

<!--Device-NotificationRequest-notificationFlags?: NotificationFlags--><!--Device-NotificationRequest-notificationFlags?: NotificationFlags-End-->

**System capability:** SystemCapability.Notification.Notification

## notificationSlotType

```TypeScript
notificationSlotType?: notificationManager.SlotType
```

Type of the [notification slot](../../../notification/notification-glossary.md#notification-slot). The default value is OTHER_TYPES. Different slot types have different [notification reminder modes](../../../notification/notification-glossary.md#notification-reminder-mode).

**Type:** [notificationManager.SlotType](arkts-notification-notificationmanager-slottype-e.md)

**Since:** 11

<!--Device-NotificationRequest-notificationSlotType?: notificationManager.SlotType--><!--Device-NotificationRequest-notificationSlotType?: notificationManager.SlotType-End-->

**System capability:** SystemCapability.Notification.Notification

## overlayIcon

```TypeScript
overlayIcon?: image.PixelMap
```

Overlay icon of the notification, which replaces the icon on the left of the notification. The value is empty by default. This API takes effect only when [notificationSlotType](arkts-notification-notificationrequest-i.md) is set to SOCIAL_COMMUNICATION.

The total number of bytes of the icon pixels does not exceed 192KB (the total number of bytes of the icon pixels is obtained through [getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber)). If this limit is exceeded, the setting does not take effect. The recommended icon pixel dimensions are 128*128. The actual display effect depends on device capabilities and the notification center UI style<!--RP3--><!--RP3End-->.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 23

<!--Device-NotificationRequest-overlayIcon?: image.PixelMap--><!--Device-NotificationRequest-overlayIcon?: image.PixelMap-End-->

**System capability:** SystemCapability.Notification.Notification

## priorityNotificationType

```TypeScript
priorityNotificationType?: notificationManager.PriorityNotificationType
```

Notification priority type. The default value is OTHER. Setting this parameter can pin the notification to the top and display it prominently in the [notification center](../../../notification/notification-glossary.md#notification-center). <!--RP2--><!--RP2End--> The actual display effect depends on device capabilities and the notification center UI style.

**Type:** [notificationManager.PriorityNotificationType](arkts-notification-notificationmanager-prioritynotificationtype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-NotificationRequest-priorityNotificationType?: notificationManager.PriorityNotificationType--><!--Device-NotificationRequest-priorityNotificationType?: notificationManager.PriorityNotificationType-End-->

**System capability:** SystemCapability.Notification.Notification

## removalWantAgent

```TypeScript
removalWantAgent?: WantAgent
```

Behavior intent of an application, which is triggered when a notification is removed. This parameter is left empty by default.

Currently, redirection to UIAbility is not supported. Only common events can be published (that is, the **actionType** field of [WantAgentInfo](../../apis-ability-kit/arkts-apis/arkts-ability-wantagentinfo-i.md) is set to **4**).

**Type:** [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md)

**Since:** 9

<!--Device-NotificationRequest-removalWantAgent?: WantAgent--><!--Device-NotificationRequest-removalWantAgent?: WantAgent-End-->

**System capability:** SystemCapability.Notification.Notification

## showDeliveryTime

```TypeScript
showDeliveryTime?: boolean
```

Whether to display the time when the notification is delivered. Not supported currently.

**Type:** boolean

**Since:** 7

<!--Device-NotificationRequest-showDeliveryTime?: boolean--><!--Device-NotificationRequest-showDeliveryTime?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## smallIcon

```TypeScript
smallIcon?: image.PixelMap
```

Icon on the left of the notification. The value is empty by default. It is automatically generated by the system and does not need to be configured by the developer.

The total number of bytes of the icon pixels does not exceed 192KB (the total number of bytes of the icon pixels is obtained through [getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber)). If this limit is exceeded, the setting does not take effect. The recommended icon pixel dimensions are 128*128. The actual display effect depends on device capabilities and the notification center UI style<!--RP4--><!--RP4End-->.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 7

<!--Device-NotificationRequest-smallIcon?: image.PixelMap--><!--Device-NotificationRequest-smallIcon?: image.PixelMap-End-->

**System capability:** SystemCapability.Notification.Notification

## sound

```TypeScript
sound?: string
```

Resource path of the application notification [customized ringtone](../../../notification/notification-glossary.md#customized-ringtone). The value is empty by default. Two audio resource sources are supported:

- Resource file: a preset audio file of the application. The resource file must be placed in the resources/rawfile  
directory, and the file name is passed in directly when used.  
- Sandbox file: an audio file downloaded from the network or generated by the user. It must be placed in the files  
directory or its subdirectories in the EL1 area of the [sandbox file directory](../../../file-management/app-sandbox-directory.md#application-file-directory-and-application-file-path). The format passed in is uri::{fileUri}, where fileUri is the path obtained through [getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md). For example, the application passes the downloaded audio resource demo.mp3 into the sandbox file directory /data/storage/el1/base/files/, and the path obtained through getUriFromPath is file://{bundleName}/data/storage/el1/base/files/demo.mp3. Publishing a notification with this path plays the audio resource downloaded by the application.

Formats such as m4a, aac, mp3, ogg, wav, flac, and amr are supported.

**Type:** string

**Since:** 12

<!--Device-NotificationRequest-sound?: string--><!--Device-NotificationRequest-sound?: string-End-->

**System capability:** SystemCapability.Notification.Notification

## tapDismissed

```TypeScript
tapDismissed?: boolean
```

Whether the notification is automatically cleared when the notification carries **wantAgent** or **actionButtons**. This parameter is valid only when the notification carries **wantAgent** or **actionButtons**. The default value is **true**.

- **true**: The current notification is automatically cleared after the notification or button is tapped.  
- **false**: The current notification is retained after the notification or button is tapped.

**Type:** boolean

**Since:** 7

<!--Device-NotificationRequest-tapDismissed?: boolean--><!--Device-NotificationRequest-tapDismissed?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## template

```TypeScript
template?: NotificationTemplate
```

Notification template. This parameter is left empty by default.

**Type:** [NotificationTemplate](arkts-notification-notificationtemplate-i.md)

**Since:** 8

<!--Device-NotificationRequest-template?: NotificationTemplate--><!--Device-NotificationRequest-template?: NotificationTemplate-End-->

**System capability:** SystemCapability.Notification.Notification

## updateOnly

```TypeScript
updateOnly?: boolean
```

Whether to update notifications only. The default value is **false**.

- **true**: If a notification with the same ID exists, the notification is updated. If no notification with the  
same ID exists, the update fails and no new notification is created.  
- **false**: If a notification with the same ID exists, the notification is updated. If no notification with the  
same ID exists, a new notification is created.

**Type:** boolean

**Since:** 18

<!--Device-NotificationRequest-updateOnly?: boolean--><!--Device-NotificationRequest-updateOnly?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

Behavior intent of an application, which is triggered when a notification is clicked. This parameter is left empty by default.

**Type:** [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md)

**Since:** 7

<!--Device-NotificationRequest-wantAgent?: WantAgent--><!--Device-NotificationRequest-wantAgent?: WantAgent-End-->

**System capability:** SystemCapability.Notification.Notification

## slotType

```TypeScript
slotType?: notification.SlotType
```

Notification slot type. The default value is **OTHER_TYPES**.

**Type:** [notification.SlotType](arkts-notification-notification-slottype-depr-e.md)

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [notificationSlotType](#notificationslottype)

<!--Device-NotificationRequest-slotType?: notification.SlotType--><!--Device-NotificationRequest-slotType?: notification.SlotType-End-->

**System capability:** SystemCapability.Notification.Notification
