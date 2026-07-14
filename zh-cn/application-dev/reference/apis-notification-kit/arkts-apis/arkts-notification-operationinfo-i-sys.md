# OperationInfo（系统接口）

跨设备协同操作信息。

**起始版本：** 18

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { notificationSubscribe } from '@kit.NotificationKit';
```

## actionName

```TypeScript
actionName?: string
```

描述通知中显示的操作按钮（与通知
[NotificationActionButton](arkts-notification-notificationactionbutton-i.md)中title字段保持一致）。

**类型：** string

**起始版本：** 18

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## buttonIndex

```TypeScript
buttonIndex?: number
```

用户点击的非实况通知按钮序号或实况通知辅助区序号。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## operationType

```TypeScript
operationType?: number
```

用户点击操作类型。

- 0：用户点击非实况通知本体。
- 1：用户点击非实况通知按钮。
- 32：用户点击实况通知本体。
- 33：用户点击实况通知辅助区

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## userInput

```TypeScript
userInput?: string
```

用户输入（用于通知跨设备快捷回复场景传递用户输入，与通知
[NotificationUserInput](arkts-notification-notificationuserinput-i.md)中inputKey字段保持一致）。

**类型：** string

**起始版本：** 18

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

