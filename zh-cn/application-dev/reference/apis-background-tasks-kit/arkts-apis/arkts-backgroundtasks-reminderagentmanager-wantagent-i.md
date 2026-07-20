# WantAgent

跳转目标的ability信息。

**起始版本：** 9

<!--Device-reminderAgentManager-interface WantAgent--><!--Device-reminderAgentManager-interface WantAgent-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## abilityName

```TypeScript
abilityName: string
```

指明跳转目标的ability名称。

**类型：** string

**起始版本：** 9

<!--Device-WantAgent-abilityName: string--><!--Device-WantAgent-abilityName: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## parameters

```TypeScript
parameters?: Record<string, Object>
```

需要传递到目标的参数。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 12

<!--Device-WantAgent-parameters?: Record<string, Object>--><!--Device-WantAgent-parameters?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## pkgName

```TypeScript
pkgName: string
```

指明跳转目标的包名。

**类型：** string

**起始版本：** 9

<!--Device-WantAgent-pkgName: string--><!--Device-WantAgent-pkgName: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## uri

```TypeScript
uri?: string
```

指明跳转目标的uri信息。

**类型：** string

**起始版本：** 12

<!--Device-WantAgent-uri?: string--><!--Device-WantAgent-uri?: string-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

