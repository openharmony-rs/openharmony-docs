# NotificationCheckInfo (System API)

```TypeScript
export interface NotificationCheckInfo
```

Describes the parameters of check notifications.

**Since:** 10

<!--Device-notificationManager-export interface NotificationCheckInfo--><!--Device-notificationManager-export interface NotificationCheckInfo-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Since:** 10

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-bundleName: string--><!--Device-NotificationCheckInfo-bundleName: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## contentType

```TypeScript
contentType: ContentType
```

Notification type.

**Type:** [ContentType](arkts-notification-notificationmanager-contenttype-e.md)

**Since:** 10

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-contentType: ContentType--><!--Device-NotificationCheckInfo-contentType: ContentType-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## creatorUserId

```TypeScript
creatorUserId: number
```

User ID of the notification.

**Type:** number

**Since:** 11

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-creatorUserId: int--><!--Device-NotificationCheckInfo-creatorUserId: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## extraInfos

```TypeScript
extraInfos?: Record<string, Object>
```

Extra information about the live view.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-extraInfos?: Record<string, Object>--><!--Device-NotificationCheckInfo-extraInfos?: Record<string, Object>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## label

```TypeScript
label?: string
```

Notification label.

**Type:** string

**Since:** 11

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-label?: string--><!--Device-NotificationCheckInfo-label?: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## notificationId

```TypeScript
notificationId: number
```

Notification ID.

**Type:** number

**Since:** 10

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-notificationId: int--><!--Device-NotificationCheckInfo-notificationId: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## slotType

```TypeScript
slotType: SlotType
```

Notification slot type.

**Type:** [SlotType](arkts-notification-notificationmanager-slottype-e.md)

**Since:** 11

**Required permissions:** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-slotType: SlotType--><!--Device-NotificationCheckInfo-slotType: SlotType-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
