# ReminderInfo

代理提醒信息，包含 ReminderRequest 和 ReminderId。

**起始版本：** 23

<!--Device-reminderAgentManager-interface ReminderInfo--><!--Device-reminderAgentManager-interface ReminderInfo-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## reminderId

```TypeScript
reminderId: int
```

发布提醒后返回的id。

**类型：** int

**起始版本：** 23

<!--Device-ReminderInfo-reminderId: int--><!--Device-ReminderInfo-reminderId: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## reminderReq

```TypeScript
reminderReq: ReminderRequest
```

代理提醒对象。

**类型：** ReminderRequest

**起始版本：** 23

<!--Device-ReminderInfo-reminderReq: ReminderRequest--><!--Device-ReminderInfo-reminderReq: ReminderRequest-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

