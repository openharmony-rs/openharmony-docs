# NotificationCheckResult（系统接口）

通知校验结果。

**起始版本：** 10

<!--Device-notificationManager-export interface NotificationCheckResult--><!--Device-notificationManager-export interface NotificationCheckResult-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## code

```TypeScript
code: number
```

0-display，1-no display。

**类型：** number

**起始版本：** 10

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckResult-code: int--><!--Device-NotificationCheckResult-code: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## message

```TypeScript
message: string
```

结果信息。

**类型：** string

**起始版本：** 10

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER and ohos.permission.NOTIFICATION_AGENT_CONTROLLER

<!--Device-NotificationCheckResult-message: string--><!--Device-NotificationCheckResult-message: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

