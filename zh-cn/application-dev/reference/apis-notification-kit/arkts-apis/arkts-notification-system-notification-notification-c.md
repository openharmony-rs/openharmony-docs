# Notification

提供通知管理的能力。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

**替代接口：** [notification/notification](arkts-notification.md#@ohos.notification)

<!--Device-unnamed-declare class Notification--><!--Device-unnamed-declare class Notification-End-->

**系统能力：** SystemCapability.Notification.Notification

## 导入模块

```TypeScript
import { ActionResult, ShowNotificationOptions } from '@kit.NotificationKit';
```

## show

```TypeScript
static show(options?: ShowNotificationOptions): void
```

显示通知。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 7

**替代接口：** [notification/notification](arkts-notification.md#@ohos.notification)

<!--Device-Notification-static show(options?: ShowNotificationOptions): void--><!--Device-Notification-static show(options?: ShowNotificationOptions): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ShowNotificationOptions](arkts-notification-system-notification-shownotificationoptions-i.md) | 否 | 通知标题。 |

