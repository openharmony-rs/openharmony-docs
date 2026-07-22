# NotificationSubscribeInfo（系统接口）

通知发布者的信息。
> **说明：**  
>  
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。  
>  
> 本模块为系统接口。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationSubscribeInfo--><!--Device-unnamed-export interface NotificationSubscribeInfo-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## bundleNames

```TypeScript
bundleNames?: Array<string>
```

应用Bundle名称。 不传递该参数时，默认订阅所有应用的通知。

**类型：** Array&lt;string&gt;

**起始版本：** 7

<!--Device-NotificationSubscribeInfo-bundleNames?: Array<string>--><!--Device-NotificationSubscribeInfo-bundleNames?: Array<string>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## deviceType

```TypeScript
deviceType?: string
```

设备类型。不传递该参数时，默认订阅当前设备的通知。根据[设备信息](../../apis-basic-service-kit/arkts-apis/arkts-deviceinfo.md)获取。

**类型：** string

**起始版本：** 12

<!--Device-NotificationSubscribeInfo-deviceType?: string--><!--Device-NotificationSubscribeInfo-deviceType?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## enableClassification

```TypeScript
enableClassification?: boolean
```

是否启用通知分类。  
- true：表示启用。  
- false：表示禁用。默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSubscribeInfo-enableClassification?: boolean--><!--Device-NotificationSubscribeInfo-enableClassification?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## filterLimit

```TypeScript
filterLimit?: number
```

通知过滤范围。默认值为0。取值范围包括：

- 0：不进行任何过滤，订阅全部通知。  
- 1：将渠道类型为[SOCIAL_COMMUNICATION](arkts-notification-notificationmanager-slottype-e.md)且[userInput](arkts-notification-notificationactionbutton-notificationactionbutton-i.md)为空的通知过滤掉。  
- 2：将渠道类型为[SOCIAL_COMMUNICATION](arkts-notification-notificationmanager-slottype-e.md)且[userInput](arkts-notification-notificationactionbutton-notificationactionbutton-i.md)不为空的通知过滤掉。

**类型：** number

**起始版本：** 18

<!--Device-NotificationSubscribeInfo-filterLimit?: long--><!--Device-NotificationSubscribeInfo-filterLimit?: long-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## needSilentReplayOnSubscribe

```TypeScript
needSilentReplayOnSubscribe?: boolean
```

是否启用订阅时的静默重放。  
- true：表示启用。  
- false：表示禁用。默认值为false。启用后，首次订阅时会以静默方式重新推送历史通知，不会出现响铃和振动提醒。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSubscribeInfo-needSilentReplayOnSubscribe?: boolean--><!--Device-NotificationSubscribeInfo-needSilentReplayOnSubscribe?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## pictureOptions

```TypeScript
pictureOptions?: PictureOptions
```

实况通知图片配置项。

**类型：** PictureOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSubscribeInfo-pictureOptions?: PictureOptions--><!--Device-NotificationSubscribeInfo-pictureOptions?: PictureOptions-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## slotTypes

```TypeScript
slotTypes?: Array<notificationManager.SlotType>
```

通知渠道类型。 不传递该参数时，默认订阅所有渠道类型的通知。

**类型：** Array&lt;notificationManager.SlotType&gt;

**起始版本：** 18

<!--Device-NotificationSubscribeInfo-slotTypes?: Array<notificationManager.SlotType>--><!--Device-NotificationSubscribeInfo-slotTypes?: Array<notificationManager.SlotType>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

用户ID。 不传递该参数时，默认订阅当前用户ID的通知。

**类型：** number

**起始版本：** 7

<!--Device-NotificationSubscribeInfo-userId?: int--><!--Device-NotificationSubscribeInfo-userId?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## voiceContentOptions

```TypeScript
voiceContentOptions?: VoiceContentOptions
```

订阅通知的语音播报内容配置项。

**类型：** VoiceContentOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotificationSubscribeInfo-voiceContentOptions?: VoiceContentOptions--><!--Device-NotificationSubscribeInfo-voiceContentOptions?: VoiceContentOptions-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

