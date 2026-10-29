# Notification

```TypeScript
declare class Notification
```

Manages notifications.

**起始版本：** 3

**废弃版本：** 7

**替代接口：** [notification/notification](arkts-notification-notification.md)

<!--Device-unnamed-declare class Notification--><!--Device-unnamed-declare class Notification-End-->

**系统能力：** SystemCapability.Notification.Notification

## 导入模块

```TypeScript
import { Notification, ActionResult, ShowNotificationOptions } from '@kit.NotificationKit';
```

## show

```TypeScript
static show(options?: ShowNotificationOptions): void
```

显示通知。

**起始版本：** 3

**废弃版本：** 7

**替代接口：** [notification/notification](arkts-notification-notification.md)

<!--Device-Notification-static show(options?: ShowNotificationOptions): void--><!--Device-Notification-static show(options?: ShowNotificationOptions): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShowNotificationOptions](arkts-notification-system-notification-shownotificationoptions-i.md) | 否 | 通知展示的相关参数选项，可设置通知标题、通知内容以及通知被点击后触发的行为。 |

**示例**

```TypeScript
let notificationObj: notification = {
  show() {
    notification.show({
      contentTitle: 'title info',
      contentText: 'text',
      clickAction: {
        bundleName: 'com.example.testapp',
        abilityName: 'notificationDemo',
        uri: '/path/to/notification'
      }
    });
  }
}
```
