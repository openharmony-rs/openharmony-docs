# NotificationMultiLineContent

描述多行文本通知。继承自[NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)。

> **说明：**  
>  
> - 当该类型通知与其他通知形成组通知时，该通知类型的展示效果默认为折叠态，  
> 显示的标题与正文为该类型继承的NotificationBasicContent中的`title`与`text`。  
> 当该类型通知单独展示，没有与其他通知形成组通知时，该通知类型的展示效果  
> 默认为展开态，显示的标题为展开时的标题`longTitle`，多行文本内容`lines`作为正文多行显示。  
>  
> - 用户点击成组展示的通知，查看各个通知详情时，该通知的展示效果变化为展开态。  
>  
> - 实际显示效果依赖于设备能力和通知中心UI样式。

**继承/实现关系：** NotificationMultiLineContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**起始版本：** 7

<!--Device-unnamed-export interface NotificationMultiLineContent extends NotificationBasicContent--><!--Device-unnamed-export interface NotificationMultiLineContent extends NotificationBasicContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## briefText

```TypeScript
briefText: string
```

通知概要内容，是对通知内容的总结，不在通知中心中显示。不可为空字符串，大小不超过1024字节，超出部分会被截断。

**类型：** string

**起始版本：** 7

<!--Device-NotificationMultiLineContent-briefText: string--><!--Device-NotificationMultiLineContent-briefText: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## lines

```TypeScript
lines: Array<string>
```

通知展开后显示的多行文本列表，每行作为独立条目展示，最多支持三行。每行大小不超过1024字节，超出部分会被截断。

**类型：** Array<string>

**起始版本：** 7

<!--Device-NotificationMultiLineContent-lines: Array<string>--><!--Device-NotificationMultiLineContent-lines: Array<string>-End-->

**系统能力：** SystemCapability.Notification.Notification

## longTitle

```TypeScript
longTitle: string
```

通知展开时的标题。不可为空字符串，大小不超过1024字节，超出部分会被截断。

**类型：** string

**起始版本：** 7

<!--Device-NotificationMultiLineContent-longTitle: string--><!--Device-NotificationMultiLineContent-longTitle: string-End-->

**系统能力：** SystemCapability.Notification.Notification

