# NotificationSubscribeInfo (System API)

```TypeScript
export interface NotificationSubscribeInfo
```

The **NotificationSubscribeInfo** module provides APIs for defining the information about the publisher for notification subscription.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## bundleNames

```TypeScript
bundleNames?: Array<string>
```

Bundle names of the applications whose notifications to subscribe to. If this parameter is not specified, the subscription defaults to notifications from all applications.

**Type:** Array&lt;string&gt;

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## deviceType

```TypeScript
deviceType?: string
```

Device type. If this parameter is not specified, the subscription defaults to notifications from the current device. The value is obtained based on [device information](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-deviceinfo.md).

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## enableClassification

```TypeScript
enableClassification?: boolean
```

Whether to enable notification classification.

- **true**: yes.  
- **false**: no. The default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## filterLimit

```TypeScript
filterLimit?: number
```

Notification filtering range. The default value is **0**. The options are as follows:

- **0**: All notifications are included in the subscription.  
- **1**: Filter out notifications whose slot type is [SOCIAL_COMMUNICATION](arkts-notification-notificationmanager-slottype-e.md) and [userInput](arkts-notification-notificationactionbutton-notificationactionbutton-i.md) is empty.  
- **2**: Filter out notifications whose slot type is [SOCIAL_COMMUNICATION](arkts-notification-notificationmanager-slottype-e.md) and [userInput](arkts-notification-notificationactionbutton-notificationactionbutton-i.md) is not empty.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## needSilentReplayOnSubscribe

```TypeScript
needSilentReplayOnSubscribe?: boolean
```

Whether to enable silent replay upon subscription.

- **true**: yes.  
- **false**: no. The default value is **false**.

After this feature is enabled, historical notifications are silently re-pushed upon the first subscription, without ringing or vibration reminders.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## pictureOptions

```TypeScript
pictureOptions?: PictureOptions
```

Image options of the live notification.

**Type:** [PictureOptions](arkts-notification-notificationsubscribeinfo-pictureoptions-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## slotTypes

```TypeScript
slotTypes?: Array<notificationManager.SlotType>
```

Types of the notification slots. If this parameter is not specified, the subscription defaults to notifications of all slot types.

**Type:** Array&lt;[notificationManager.SlotType](arkts-notification-notificationmanager-slottype-e.md)&gt;

**Since:** 18

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

User ID. If this parameter is not specified, the subscription defaults to notifications from the current user ID.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## voiceContentOptions

```TypeScript
voiceContentOptions?: VoiceContentOptions
```

Configuration options for notification voice broadcast.

**Type:** [VoiceContentOptions](arkts-notification-notificationsubscribeinfo-voicecontentoptions-i-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
