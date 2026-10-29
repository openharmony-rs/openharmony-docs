# RingtoneInfo（系统接口）

```TypeScript
export interface RingtoneInfo
```

描述[自定义铃声](../../../notification/notification-glossary.md#customized-ringtone自定义铃声)信息。

**起始版本：** 21

<!--Device-notificationManager-export interface RingtoneInfo--><!--Device-notificationManager-export interface RingtoneInfo-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## ringtoneFileName

```TypeScript
ringtoneFileName?: string
```

铃声的文件名称。

大小不超过202字节，超出后返回401错误码。默认为空。

**类型：** string

**起始版本：** 21

<!--Device-RingtoneInfo-ringtoneFileName?: string--><!--Device-RingtoneInfo-ringtoneFileName?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## ringtoneTitle

```TypeScript
ringtoneTitle?: string
```

铃声的标题。

大小不超过202字节，超出后返回401错误码。默认为空。

**类型：** string

**起始版本：** 21

<!--Device-RingtoneInfo-ringtoneTitle?: string--><!--Device-RingtoneInfo-ringtoneTitle?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## ringtoneType

```TypeScript
ringtoneType: RingtoneType
```

铃声的类型。

**类型：** [RingtoneType](arkts-notification-notificationmanager-ringtonetype-e-sys.md)

**起始版本：** 21

<!--Device-RingtoneInfo-ringtoneType: RingtoneType--><!--Device-RingtoneInfo-ringtoneType: RingtoneType-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## ringtoneUri

```TypeScript
ringtoneUri?: string
```

铃声的URI。资源支持可参考[media.AVPlayer](../../apis-media/arkts-apis/arkts-media-media-avplayer-i.md)。

大小不超过202字节，超出后返回401错误码。默认为空。

**类型：** string

**起始版本：** 21

<!--Device-RingtoneInfo-ringtoneUri?: string--><!--Device-RingtoneInfo-ringtoneUri?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。
