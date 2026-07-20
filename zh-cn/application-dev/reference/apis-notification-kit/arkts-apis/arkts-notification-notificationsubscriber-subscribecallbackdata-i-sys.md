# SubscribeCallbackData（系统接口）

返回携带系统属性值的通知信息。

**起始版本：** 7

<!--Device-unnamed-export interface SubscribeCallbackData--><!--Device-unnamed-export interface SubscribeCallbackData-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## notificationClassification

```TypeScript
readonly notificationClassification?: NotificationClassification
```

通知分类信息。仅在[NotificationSubscribeInfo](arkts-notification-notificationsubscribeinfo-notificationsubscribeinfo-i-sys.md)中的enableClassification为true时存在。

**类型：** NotificationClassification

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubscribeCallbackData-readonly notificationClassification?: NotificationClassification--><!--Device-SubscribeCallbackData-readonly notificationClassification?: NotificationClassification-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## reason

```TypeScript
readonly reason?: number
```

删除原因（1:点击通知后删除通知，2:用户删除通知） 。

**类型：** number

**起始版本：** 7

<!--Device-SubscribeCallbackData-readonly reason?: int--><!--Device-SubscribeCallbackData-readonly reason?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## request

```TypeScript
readonly request: NotificationRequest
```

通知内容。

**类型：** NotificationRequest

**起始版本：** 7

<!--Device-SubscribeCallbackData-readonly request: NotificationRequest--><!--Device-SubscribeCallbackData-readonly request: NotificationRequest-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## sortingMap

```TypeScript
readonly sortingMap?: NotificationSortingMap
```

通知排序信息。

**类型：** NotificationSortingMap

**起始版本：** 7

<!--Device-SubscribeCallbackData-readonly sortingMap?: NotificationSortingMap--><!--Device-SubscribeCallbackData-readonly sortingMap?: NotificationSortingMap-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## sound

```TypeScript
readonly sound?: string
```

通知声音。

**类型：** string

**起始版本：** 7

<!--Device-SubscribeCallbackData-readonly sound?: string--><!--Device-SubscribeCallbackData-readonly sound?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## vibrationValues

```TypeScript
readonly vibrationValues?: Array<number>
```

通知振动。

**类型：** Array&lt;number&gt;

**起始版本：** 7

<!--Device-SubscribeCallbackData-readonly vibrationValues?: Array<long>--><!--Device-SubscribeCallbackData-readonly vibrationValues?: Array<long>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## voiceContent

```TypeScript
voiceContent?: VoiceContent
```

通知语音播报内容。

**类型：** VoiceContent

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SubscribeCallbackData-voiceContent?: VoiceContent--><!--Device-SubscribeCallbackData-voiceContent?: VoiceContent-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

