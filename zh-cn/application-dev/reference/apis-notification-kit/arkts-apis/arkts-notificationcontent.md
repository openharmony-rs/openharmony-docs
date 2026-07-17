# notificationContent (Some notification types and content)

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md) | 描述普通文本通知，用于展示标题和正文内容，是其他通知类型的基础内容结构。其他通知类型（如长文本、多行文本、图片、实况窗）均继承本接口，在此基础上扩展各自特有字段。 |
| [NotificationButton](arkts-notification-notificationcontent-notificationbutton-i.md) | 描述通知按钮，用于在实况窗中展示可交互的按钮。 |
| [NotificationCapsule](arkts-notification-notificationcontent-notificationcapsule-i.md) | 描述通知胶囊，用于在实况窗中展示胶囊形态。 |
| [NotificationContent](arkts-notification-notificationcontent-notificationcontent-i.md) | 通知内容。 |
| [NotificationLongTextContent](arkts-notification-notificationcontent-notificationlongtextcontent-i.md) | 描述长文本通知。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)。 |
| [NotificationMultiLineContent](arkts-notification-notificationcontent-notificationmultilinecontent-i.md) | 描述多行文本通知。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)。 |
| [NotificationPictureContent](arkts-notification-notificationcontent-notificationpicturecontent-i.md) | 描述附有图片的通知。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)。 |
| [NotificationProgress](arkts-notification-notificationcontent-notificationprogress-i.md) | 描述通知进度，用于在实况窗中展示进度条信息。 |
| [NotificationSystemLiveViewContent](arkts-notification-notificationcontent-notificationsystemliveviewcontent-i.md) | 描述系统实况窗通知内容，用于在实况窗中展示实时状态信息。不支持三方应用直接创建该类型通知，可以由系统代理创建系统实况窗类型通知后，三方应用发布同ID的通知来更新指定内容。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)。 |
| [NotificationTime](arkts-notification-notificationcontent-notificationtime-i.md) | 描述通知计时信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i-sys.md) | 描述普通文本通知，用于展示标题和正文内容，是其他通知类型的基础内容结构。其他通知类型（如长文本、多行文本、图片、实况窗）均继承本接口，在此基础上扩展各自特有字段。 |
| [NotificationCapsule](arkts-notification-notificationcontent-notificationcapsule-i-sys.md) | 描述通知胶囊，用于在实况窗中展示胶囊形态。 |
| [NotificationContent](arkts-notification-notificationcontent-notificationcontent-i-sys.md) | 通知内容。 |
| [NotificationIconButton](arkts-notification-notificationcontent-notificationiconbutton-i-sys.md) | 描述系统通知按钮。 |
| [NotificationLiveViewContent](arkts-notification-notificationcontent-notificationliveviewcontent-i-sys.md) | 描述普通实况通知。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)。 |
| [NotificationMultiLineContent](arkts-notification-notificationcontent-notificationmultilinecontent-i-sys.md) | 描述多行文本通知。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)。 |
| [NotificationSystemLiveViewContent](arkts-notification-notificationcontent-notificationsystemliveviewcontent-i-sys.md) | 描述系统实况窗通知内容，用于在实况窗中展示实时状态信息。不支持三方应用直接创建该类型通知，可以由系统代理创建系统实况窗类型通知后，三方应用发布同ID的通知来更新指定内容。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LiveViewStatus](arkts-notification-notificationcontent-liveviewstatus-e-sys.md) | 描述普通实况通知的状态。 |
| [LiveViewTypes](arkts-notification-notificationcontent-liveviewtypes-e-sys.md) | 描述实况通知的类型。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IconType](arkts-notification-icontype-t-sys.md) | 描述图标的类型。 |
<!--DelEnd-->

