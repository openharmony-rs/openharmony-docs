# NotificationRequest

定义了通知请求的数据结构，用于描述一条通知的全部信息，包括通知内容、标识、展示样式、交互行为等。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationRequest--><!--Device-unnamed-export interface NotificationRequest-End-->

**系统能力：** SystemCapability.Notification.Notification

## actionButtons

```TypeScript
actionButtons?: Array<NotificationActionButton>
```

通知按钮，默认为空。一条通知中最多包含两个按钮。从API version 16开始，`wearable`设备一条通知最多包含三个按钮。

**类型：** Array&lt;NotificationActionButton&gt;

**起始版本：** 7

<!--Device-NotificationRequest-actionButtons?: Array<NotificationActionButton>--><!--Device-NotificationRequest-actionButtons?: Array<NotificationActionButton>-End-->

**系统能力：** SystemCapability.Notification.Notification

## appMessageId

```TypeScript
appMessageId?: string
```

应用发送通知携带的唯一标识字段，用于通知去重。如果同一应用通过本地和云端等不同途径发布携带相同appMessageId的通知，设备只展示一条消息，之后收到的重复通知会被静默去重，不展示、不提醒。去重标识仅在通知发布的24小时内有效，超过24小时或者设备重启失效。大小不超过202字节，超出部分会被截断。默认为空。

**类型：** string

**起始版本：** 12

<!--Device-NotificationRequest-appMessageId?: string--><!--Device-NotificationRequest-appMessageId?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## autoDeletedTime

```TypeScript
autoDeletedTime?: number
```

通知定时清除时间。设置该参数可使通知在指定时间后自动清除。默认值为0。

数据格式：时间戳。

单位：毫秒。

例如，希望某通知存留3秒（3000ms）后对其进行清除，则对应的清除时间为：new Date().getTime() + 3000。

**类型：** number

**起始版本：** 7

<!--Device-NotificationRequest-autoDeletedTime?: long--><!--Device-NotificationRequest-autoDeletedTime?: long-End-->

**系统能力：** SystemCapability.Notification.Notification

## badgeIconStyle

```TypeScript
badgeIconStyle?: number
```

通知角标类型。预留能力，暂未支持。

**类型：** number

**起始版本：** 7

<!--Device-NotificationRequest-badgeIconStyle?: int--><!--Device-NotificationRequest-badgeIconStyle?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

## badgeNumber

```TypeScript
badgeNumber?: number
```

应用程序图标上显示的通知数，该数量累计展示，默认值为0。

当`badgeNumber`取值小于或等于0时，将忽略本次角标设定。

当角标累加设定个数取值大于99时，通知角标将显示99+。

例如，应用发布3条通知，`badgeNumber`依次设置为2、0、3，应用将依次展示为2、2、5。

**类型：** number

**起始版本：** 9

<!--Device-NotificationRequest-badgeNumber?: long--><!--Device-NotificationRequest-badgeNumber?: long-End-->

**系统能力：** SystemCapability.Notification.Notification

## color

```TypeScript
color?: number
```

通知背景颜色。预留能力，暂未支持。

**类型：** number

**起始版本：** 7

<!--Device-NotificationRequest-color?: long--><!--Device-NotificationRequest-color?: long-End-->

**系统能力：** SystemCapability.Notification.Notification

## colorEnabled

```TypeScript
colorEnabled?: boolean
```

通知背景颜色是否使能。预留能力，暂未支持。

**类型：** boolean

**起始版本：** 7

<!--Device-NotificationRequest-colorEnabled?: boolean--><!--Device-NotificationRequest-colorEnabled?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## content

```TypeScript
content: NotificationContent
```

通知展示内容。包括通知标题、正文等。

**类型：** NotificationContent

**起始版本：** 7

<!--Device-NotificationRequest-content: NotificationContent--><!--Device-NotificationRequest-content: NotificationContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## creatorBundleName

```TypeScript
readonly creatorBundleName?: string
```

创建通知的应用名称。

**类型：** string

**起始版本：** 7

<!--Device-NotificationRequest-readonly creatorBundleName?: string--><!--Device-NotificationRequest-readonly creatorBundleName?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## creatorPid

```TypeScript
readonly creatorPid?: number
```

创建通知的PID。

**类型：** number

**起始版本：** 7

<!--Device-NotificationRequest-readonly creatorPid?: int--><!--Device-NotificationRequest-readonly creatorPid?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

## creatorUid

```TypeScript
readonly creatorUid?: number
```

创建通知的应用UID。

**类型：** number

**起始版本：** 7

<!--Device-NotificationRequest-readonly creatorUid?: int--><!--Device-NotificationRequest-readonly creatorUid?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

## creatorUserId

```TypeScript
readonly creatorUserId?: number
```

创建通知的用户ID。

**类型：** number

**起始版本：** 8

<!--Device-NotificationRequest-readonly creatorUserId?: int--><!--Device-NotificationRequest-readonly creatorUserId?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

## deliveryTime

```TypeScript
deliveryTime?: number
```

通知发送时间。系统自动生成，无需开发者配置。

数据格式：时间戳。

单位：毫秒。

**类型：** number

**起始版本：** 7

<!--Device-NotificationRequest-deliveryTime?: long--><!--Device-NotificationRequest-deliveryTime?: long-End-->

**系统能力：** SystemCapability.Notification.Notification

## distributedOption

```TypeScript
distributedOption?: DistributedOptions
```

分布式通知的选项。预留能力，暂未支持。

**类型：** DistributedOptions

**起始版本：** 8

<!--Device-NotificationRequest-distributedOption?: DistributedOptions--><!--Device-NotificationRequest-distributedOption?: DistributedOptions-End-->

**系统能力：** SystemCapability.Notification.Notification

## extraInfo

```TypeScript
extraInfo?: { [key: string]: any }
```

扩展参数。为应用提供定制服务。默认为空。

以下Key由系统赋值，开发者手动修改也不会生效，系统在数据传递时会自动修改为实际值。

- 'ohos.notificationManager.wantUri'：用户点击通知时传递给应用的[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) 中的uri字段，使用[getActiveNotifications](arkts-notification-notification-getactivenotifications-depr-f.md#getactivenotifications-1)接口获取该信息。

**类型：** { [key: string]: any }

**起始版本：** 7

<!--Device-NotificationRequest-extraInfo?: { [key: string]: any }--><!--Device-NotificationRequest-extraInfo?: { [key: string]: any }-End-->

**系统能力：** SystemCapability.Notification.Notification

## groupName

```TypeScript
groupName?: string
```

通知所属组。当不同通知的groupName相同时，这些通知将成组展示。大小不超过202字节，超出部分会被截断。默认为空。

**类型：** string

**起始版本：** 8

<!--Device-NotificationRequest-groupName?: string--><!--Device-NotificationRequest-groupName?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## hashCode

```TypeScript
readonly hashCode?: string
```

通知唯一标识。

**类型：** string

**起始版本：** 7

<!--Device-NotificationRequest-readonly hashCode?: string--><!--Device-NotificationRequest-readonly hashCode?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## id

```TypeScript
id?: number
```

通知ID，默认值为0。若已存在相同ID的通知，则更新该通知；若不存在相同ID的通知，则创建新的通知。

**类型：** number

**起始版本：** 7

<!--Device-NotificationRequest-id?: int--><!--Device-NotificationRequest-id?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

## isAlertOnce

```TypeScript
isAlertOnce?: boolean
```

发布或更新该通知时，是否只进行一次通知提醒，默认值为false。

- true：仅首次发布通知时进行提醒，后续更新该通知时，提醒方式变更为[LEVEL_LOW](arkts-notification-notificationmanager-slotlevel-e.md)。  
- false：每次均按照配置的通知提醒方式进行提醒。

**类型：** boolean

**起始版本：** 7

<!--Device-NotificationRequest-isAlertOnce?: boolean--><!--Device-NotificationRequest-isAlertOnce?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## isCountDown

```TypeScript
isCountDown?: boolean
```

是否显示倒计时时间。预留能力，暂未支持。

**类型：** boolean

**起始版本：** 7

<!--Device-NotificationRequest-isCountDown?: boolean--><!--Device-NotificationRequest-isCountDown?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## isFloatingIcon

```TypeScript
isFloatingIcon?: boolean
```

是否显示状态栏图标。预留能力，暂未支持。

**类型：** boolean

**起始版本：** 7

<!--Device-NotificationRequest-isFloatingIcon?: boolean--><!--Device-NotificationRequest-isFloatingIcon?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## isOngoing

```TypeScript
isOngoing?: boolean
```

预留能力，暂未支持。

**类型：** boolean

**起始版本：** 7

<!--Device-NotificationRequest-isOngoing?: boolean--><!--Device-NotificationRequest-isOngoing?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## isStopwatch

```TypeScript
isStopwatch?: boolean
```

是否显示已用时间。预留能力，暂未支持。

**类型：** boolean

**起始版本：** 7

<!--Device-NotificationRequest-isStopwatch?: boolean--><!--Device-NotificationRequest-isStopwatch?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## isUnremovable

```TypeScript
isUnremovable?: boolean
```

预留能力，暂未支持。

**类型：** boolean

**起始版本：** 7

<!--Device-NotificationRequest-isUnremovable?: boolean--><!--Device-NotificationRequest-isUnremovable?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## label

```TypeScript
label?: string
```

通知标签。

label字段的功能类似于id，可以单独使用，也可与id结合共同作为通知的标识。优先推荐使用id。

如果发布通知时label不为空，那么在更新或删除该通知时，也需要指定相应的label。大小不超过202字节，超出部分会被截断。默认为空。

**类型：** string

**起始版本：** 7

<!--Device-NotificationRequest-label?: string--><!--Device-NotificationRequest-label?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## largeIcon

```TypeScript
largeIcon?: image.PixelMap
```

通知大图标，默认为空。图标像素的总字节数不超过192KB（图标像素的总字节数通过[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1)获取），建议图标像素长宽为128*128。实际显示效果依赖于设备能力和通知中心UI样式。

**类型：** image.PixelMap

**起始版本：** 7

<!--Device-NotificationRequest-largeIcon?: image.PixelMap--><!--Device-NotificationRequest-largeIcon?: image.PixelMap-End-->

**系统能力：** SystemCapability.Notification.Notification

## notificationFlags

```TypeScript
notificationFlags?: NotificationFlags
```

设置或获取NotificationFlags，默认为空。从API version 23开始成为可写参数，设置该参数可削减通知的提醒方式，当通知渠道类型为[LIVE_VIEW](arkts-notification-notificationmanager-slottype-e.md)时，该参数设置不生效。

**类型：** NotificationFlags

**起始版本：** 8

<!--Device-NotificationRequest-notificationFlags?: NotificationFlags--><!--Device-NotificationRequest-notificationFlags?: NotificationFlags-End-->

**系统能力：** SystemCapability.Notification.Notification

## notificationSlotType

```TypeScript
notificationSlotType?: notificationManager.SlotType
```

通知渠道类型，默认值为OTHER_TYPES。不同渠道类型的通知提醒方式不同。

**类型：** notificationManager.SlotType

**起始版本：** 11

<!--Device-NotificationRequest-notificationSlotType?: notificationManager.SlotType--><!--Device-NotificationRequest-notificationSlotType?: notificationManager.SlotType-End-->

**系统能力：** SystemCapability.Notification.Notification

## priorityNotificationType

```TypeScript
priorityNotificationType?: notificationManager.PriorityNotificationType
```

通知优先级类型，默认值为OTHER。设置该参数可使通知置顶，并且在通知中心以突出方式显示。<!--RP2--><!--RP2End-->实际显示效果依赖于设备能力和通知中心UI样式。

**类型：** notificationManager.PriorityNotificationType

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationRequest-priorityNotificationType?: notificationManager.PriorityNotificationType--><!--Device-NotificationRequest-priorityNotificationType?: notificationManager.PriorityNotificationType-End-->

**系统能力：** SystemCapability.Notification.Notification

## removalWantAgent

```TypeScript
removalWantAgent?: WantAgent
```

封装了应用的行为意图，移除通知时触发该行为，默认为空。

当前不支持跳转UIAbility，只支持发布公共事件（即[WantAgentInfo](../../apis-ability-kit/arkts-apis/arkts-ability-wantagentinfo-wantagentinfo-i.md)的actionType字段取值为4）。

**类型：** WantAgent

**起始版本：** 9

<!--Device-NotificationRequest-removalWantAgent?: WantAgent--><!--Device-NotificationRequest-removalWantAgent?: WantAgent-End-->

**系统能力：** SystemCapability.Notification.Notification

## showDeliveryTime

```TypeScript
showDeliveryTime?: boolean
```

是否显示分发时间。预留能力，暂未支持。

**类型：** boolean

**起始版本：** 7

<!--Device-NotificationRequest-showDeliveryTime?: boolean--><!--Device-NotificationRequest-showDeliveryTime?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## slotType

```TypeScript
slotType?: notification.SlotType
```

通知渠道类型，默认值为OTHER_TYPES。

从API version 7开始支持，从API version 11开始废弃，建议使用notificationSlotType替代。

**类型：** notification.SlotType

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [notificationSlotType](arkts-notification-notificationrequest-notificationrequest-i.md#notificationslottype)

<!--Device-NotificationRequest-slotType?: notification.SlotType--><!--Device-NotificationRequest-slotType?: notification.SlotType-End-->

**系统能力：** SystemCapability.Notification.Notification

## smallIcon

```TypeScript
smallIcon?: image.PixelMap
```

通知小图标，默认为空。图标像素的总字节数不超过192KB（图标像素的总字节数通过[getPixelBytesNumber](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md#getpixelbytesnumber-1)获取），建议图标像素长宽为128*128。实际显示效果依赖于设备能力和通知中心UI样式。

**类型：** image.PixelMap

**起始版本：** 7

<!--Device-NotificationRequest-smallIcon?: image.PixelMap--><!--Device-NotificationRequest-smallIcon?: image.PixelMap-End-->

**系统能力：** SystemCapability.Notification.Notification

## sound

```TypeScript
sound?: string
```

应用通知自定义铃声资源路径，默认为空。支持两种音频资源来源：

- 资源文件：应用预置的音频文件，资源文件必须放在放在resources/rawfile目录下，使用时直接传入文件名。  
- 沙箱文件：网络下载或者用户生成的音频文件，必须放在沙箱文件目录EL1区域的files目录或者其子目录下，传入格式为uri::{fileUri}，其中fileUri是通过[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)获取的路径。例如，应用将下载的音频资源demo.mp3传入沙箱文件目录/data/storage/el1/base/files/，通过getUriFromPath获取的路径为file://{bundleName}/data/storage/el1/base/files/demo.mp3，使用该路径发布通知即可播放应用下载的音频资源。

支持m4a、aac、mp3、ogg、wav、flac、amr等格式。

**类型：** string

**起始版本：** 12

<!--Device-NotificationRequest-sound?: string--><!--Device-NotificationRequest-sound?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## tapDismissed

```TypeScript
tapDismissed?: boolean
```

点击通知携带的wantAgent或actionButtons时，该通知是否自动清除。当通知携带wantAgent或actionButtons时该字段生效。默认值为true。

- true：点击通知或按钮后，自动删除当前通知。  
- false：点击通知或按钮后，保留当前通知。

**类型：** boolean

**起始版本：** 7

<!--Device-NotificationRequest-tapDismissed?: boolean--><!--Device-NotificationRequest-tapDismissed?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## template

```TypeScript
template?: NotificationTemplate
```

通知模板，默认为空。

**类型：** NotificationTemplate

**起始版本：** 8

<!--Device-NotificationRequest-template?: NotificationTemplate--><!--Device-NotificationRequest-template?: NotificationTemplate-End-->

**系统能力：** SystemCapability.Notification.Notification

## updateOnly

```TypeScript
updateOnly?: boolean
```

是否仅更新通知，默认值为false。

- true：若已存在相同ID的通知，则更新该通知；若不存在相同ID的通知，则更新失败，并且不创建新的通知。  
- false：若已存在相同ID的通知，则更新该通知；若不存在相同ID的通知，则创建新的通知。

**类型：** boolean

**起始版本：** 18

<!--Device-NotificationRequest-updateOnly?: boolean--><!--Device-NotificationRequest-updateOnly?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

封装了应用的行为意图，点击通知时触发该行为，默认为空。

**类型：** WantAgent

**起始版本：** 7

<!--Device-NotificationRequest-wantAgent?: WantAgent--><!--Device-NotificationRequest-wantAgent?: WantAgent-End-->

**系统能力：** SystemCapability.Notification.Notification

