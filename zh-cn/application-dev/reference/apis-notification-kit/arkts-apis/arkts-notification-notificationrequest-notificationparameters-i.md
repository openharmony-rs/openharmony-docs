# NotificationParameters

描述[NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md#NotificationRequest)中wantAgent的部分信息。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-export interface NotificationParameters--><!--Device-unnamed-export interface NotificationParameters-End-->

**系统能力：** SystemCapability.Notification.Notification

## wantAction

```TypeScript
wantAction?:string
```

应用在创建wantAgent时，传入的want的action字段，具体含义请参考[action](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md#Want)。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationParameters-wantAction?:string--><!--Device-NotificationParameters-wantAction?:string-End-->

**系统能力：** SystemCapability.Notification.Notification

## wantParameters

```TypeScript
wantParameters?:Record<string, RecordData>
```

应用在创建wantAgent时，传入的want的parameters字段，具体含义请参考[parameters](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md#Want)。

**类型：** Record&lt;string, [RecordData](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-recorddata-t.md)&gt;

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationParameters-wantParameters?:Record<string, RecordData>--><!--Device-NotificationParameters-wantParameters?:Record<string, RecordData>-End-->

**系统能力：** SystemCapability.Notification.Notification

## wantUri

```TypeScript
wantUri?:string
```

应用在创建wantAgent时，传入的want的uri字段，具体含义请参考[uri](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md#Want)。

**类型：** string

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationParameters-wantUri?:string--><!--Device-NotificationParameters-wantUri?:string-End-->

**系统能力：** SystemCapability.Notification.Notification

