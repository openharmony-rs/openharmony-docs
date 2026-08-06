# NotificationMultiLineContent

描述多行文本通知。继承自[NotificationBasicContent]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_。 > **说明：** > > - 当该类型通知与其他通知形成组通知时，该通知类型的展示效果默认为折叠态， > 显示的标题与正文为该类型继承的NotificationBasicContent中的\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_与\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_。 > 当该类型通知单独展示，没有与其他通知形成组通知时，该通知类型的展示效果 > 默认为展开态，显示的标题为展开时的标题\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_，多行文本内容\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_作为正文多行显示。 > > - 用户点击成组展示的通知，查看各个通知详情时，该通知的展示效果变化为展开态。 > > - 实际显示效果依赖于设备能力和通知中心UI样式。

**继承/实现关系：** NotificationMultiLineContent extends [NotificationBasicContent](notificationcontent-notificationbasiccontent-i.md)

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface NotificationMultiLineContent extends NotificationBasicContent--><!--Device-unnamed-export interface NotificationMultiLineContent extends NotificationBasicContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## lineWantAgents

```TypeScript
lineWantAgents?: Array<WantAgent>
```

点击多行文本中某一行文本消息触发的wantAgent。不同行的文本分别对应于不同的wantAgent。该字段配置的行数不能大于 [lines]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_字段配置的行数。默认为空。

**类型：** Array&lt;WantAgent&gt;

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationMultiLineContent-lineWantAgents?: Array<WantAgent>--><!--Device-NotificationMultiLineContent-lineWantAgents?: Array<WantAgent>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

