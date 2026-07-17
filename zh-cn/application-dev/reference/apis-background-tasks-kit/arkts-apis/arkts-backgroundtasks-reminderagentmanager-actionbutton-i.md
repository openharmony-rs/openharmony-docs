# ActionButton

弹出的提醒中按钮的类型和标题。

**起始版本：** 9

<!--Device-reminderAgentManager-interface ActionButton--><!--Device-reminderAgentManager-interface ActionButton-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## title

```TypeScript
title: string
```

按钮显示的标题。

**类型：** string

**起始版本：** 9

<!--Device-ActionButton-title: string--><!--Device-ActionButton-title: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## titleResource

```TypeScript
titleResource?: string
```

标题的资源ID，用于切换系统语言后读取对应标题信息。

**类型：** string

**起始版本：** 11

<!--Device-ActionButton-titleResource?: string--><!--Device-ActionButton-titleResource?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## type

```TypeScript
type: ActionButtonType
```

按钮的类型。

**类型：** ActionButtonType

**起始版本：** 9

<!--Device-ActionButton-type: ActionButtonType--><!--Device-ActionButton-type: ActionButtonType-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

