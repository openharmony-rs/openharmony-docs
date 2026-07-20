# NotificationCheckInfo（系统接口）

通知校验参数。

**起始版本：** 10

<!--Device-notificationManager-export interface NotificationCheckInfo--><!--Device-notificationManager-export interface NotificationCheckInfo-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle名称。

**类型：** string

**起始版本：** 10

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-bundleName: string--><!--Device-NotificationCheckInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## contentType

```TypeScript
contentType: ContentType
```

通知类型。

**类型：** ContentType

**起始版本：** 10

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-contentType: ContentType--><!--Device-NotificationCheckInfo-contentType: ContentType-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## creatorUserId

```TypeScript
creatorUserId: number
```

通知的user ID。

**类型：** number

**起始版本：** 11

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-creatorUserId: int--><!--Device-NotificationCheckInfo-creatorUserId: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## extraInfos

```TypeScript
extraInfos?: Record<string, Object>
```

实况通知的附加信息。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 11

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-extraInfos?: Record<string, Object>--><!--Device-NotificationCheckInfo-extraInfos?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## label

```TypeScript
label?: string
```

通知标签。

**类型：** string

**起始版本：** 11

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-label?: string--><!--Device-NotificationCheckInfo-label?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## notificationId

```TypeScript
notificationId: number
```

通知ID。

**类型：** number

**起始版本：** 10

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-notificationId: int--><!--Device-NotificationCheckInfo-notificationId: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## slotType

```TypeScript
slotType: SlotType
```

渠道类型。

**类型：** SlotType

**起始版本：** 11

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckInfo-slotType: SlotType--><!--Device-NotificationCheckInfo-slotType: SlotType-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

