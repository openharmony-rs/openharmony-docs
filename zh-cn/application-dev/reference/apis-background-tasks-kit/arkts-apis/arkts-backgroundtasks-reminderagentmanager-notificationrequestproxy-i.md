# NotificationRequestProxy

通知请求信息。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-reminderAgentManager-interface NotificationRequestProxy--><!--Device-reminderAgentManager-interface NotificationRequestProxy-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## appMessageId

```TypeScript
appMessageId?: string
```

应用发送通知携带的唯一标识字段，用于通知去重，默认为空。具体请参考 [NotificationRequest.appMessageId]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationRequestProxy-appMessageId?: string--><!--Device-NotificationRequestProxy-appMessageId?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## isAlertOnce

```TypeScript
isAlertOnce?: boolean
```

发布或更新该通知时，是否只进行一次通知提醒，默认为false。具体请参考 [NotificationRequest.isAlertOnce]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 - true：仅首次发布通知时进行提醒，后续更新该通知时，提醒方式变更为[LEVEL\_LOW]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_. - false：每次均按照配置的通知提醒方式进行提醒。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationRequestProxy-isAlertOnce?: boolean--><!--Device-NotificationRequestProxy-isAlertOnce?: boolean-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

