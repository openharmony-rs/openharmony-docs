# RingtoneInfo (System API)

```TypeScript
export interface RingtoneInfo
```

Describes the [customized ringtone](../../../notification/notification-glossary.md#customized-ringtone) information.

**Since:** 21

<!--Device-notificationManager-export interface RingtoneInfo--><!--Device-notificationManager-export interface RingtoneInfo-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## ringtoneFileName

```TypeScript
ringtoneFileName?: string
```

File name of the ringtone. The size cannot exceed 202 bytes; otherwise, error code 401 is returned. The default value is empty.

**Type:** string

**Since:** 21

<!--Device-RingtoneInfo-ringtoneFileName?: string--><!--Device-RingtoneInfo-ringtoneFileName?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## ringtoneTitle

```TypeScript
ringtoneTitle?: string
```

Title of the ringtone. The size cannot exceed 202 bytes; otherwise, error code 401 is returned. The default value is empty.

**Type:** string

**Since:** 21

<!--Device-RingtoneInfo-ringtoneTitle?: string--><!--Device-RingtoneInfo-ringtoneTitle?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## ringtoneType

```TypeScript
ringtoneType: RingtoneType
```

Type of the ringtone.

**Type:** [RingtoneType](arkts-notification-notificationmanager-ringtonetype-e-sys.md)

**Since:** 21

<!--Device-RingtoneInfo-ringtoneType: RingtoneType--><!--Device-RingtoneInfo-ringtoneType: RingtoneType-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## ringtoneUri

```TypeScript
ringtoneUri?: string
```

URI of the ringtone. For supported resources, see [media.AVPlayer](../../apis-media/arkts-apis/arkts-media-media-avplayer-i.md). The size cannot exceed 202 bytes; otherwise, error code 401 is returned. The default value is empty.

**Type:** string

**Since:** 21

<!--Device-RingtoneInfo-ringtoneUri?: string--><!--Device-RingtoneInfo-ringtoneUri?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
