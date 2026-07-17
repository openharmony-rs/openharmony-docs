# ActionButton

弹出的提醒中按钮的类型和标题。

**起始版本：** 9

<!--Device-reminderAgentManager-interface ActionButton--><!--Device-reminderAgentManager-interface ActionButton-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## dataShareUpdate

```TypeScript
dataShareUpdate?: DataShareUpdate
```

点击按钮将更新应用数据库。

**类型：** DataShareUpdate

**起始版本：** 11

<!--Device-ActionButton-dataShareUpdate?: DataShareUpdate--><!--Device-ActionButton-dataShareUpdate?: DataShareUpdate-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**系统接口：** 此接口为系统接口。

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

点击按钮跳转的ability信息。

**类型：** WantAgent

**起始版本：** 10

<!--Device-ActionButton-wantAgent?: WantAgent--><!--Device-ActionButton-wantAgent?: WantAgent-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**系统接口：** 此接口为系统接口。

