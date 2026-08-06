# NotificationLongTextContent

描述长文本通知。继承自[NotificationBasicContent]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_。 > **说明：** > > - 当该类型通知与其他通知形成组通知时，该通知类型的展示效果默认为折叠态， > 显示的标题与正文为该类型继承的NotificationBasicContent中的\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_与\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_。 > 当该类型通知单独展示，没有与其他通知形成组通知时，该通知类型的展示效果 > 默认为展开态，显示的标题为展开时的标题\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_，显示的正文内容为长文本\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_。 > > - 用户点击成组展示的通知，查看各个通知详情时，该通知的展示效果变化为展开态。 > > - 实际显示效果依赖于设备能力和通知中心UI样式。

**继承/实现关系：** NotificationLongTextContent extends [NotificationBasicContent](notificationcontent-notificationbasiccontent-i.md)

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface NotificationLongTextContent extends NotificationBasicContent--><!--Device-unnamed-export interface NotificationLongTextContent extends NotificationBasicContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## briefText

```TypeScript
briefText: string
```

通知概要内容，是对通知内容的总结，不在通知中心中显示。 不可为空字符串，大小不超过1024字节，超出部分会被截断。

**类型：** string

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-NotificationLongTextContent-briefText: string--><!--Device-NotificationLongTextContent-briefText: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## expandedTitle

```TypeScript
expandedTitle: string
```

通知展开时的标题。不可为空字符串，大小不超过1024字节，超出部分会被截断。

**类型：** string

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-NotificationLongTextContent-expandedTitle: string--><!--Device-NotificationLongTextContent-expandedTitle: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## longText

```TypeScript
longText: string
```

通知展开后显示的完整长文本内容。不可为空字符串，大小不超过3072字节，超出部分会被截断。

**类型：** string

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-NotificationLongTextContent-longText: string--><!--Device-NotificationLongTextContent-longText: string-End-->

**系统能力：** SystemCapability.Notification.Notification

