# ComfortReminderData（系统接口）

表示舒适提醒数据。

**继承/实现关系：** ComfortReminderData extends [UserStatusData](arkts-multimodalawareness-userstatus-userstatusdata-i-sys.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { userStatus } from '@kit.MultimodalAwarenessKit';
```

## eventType

```TypeScript
eventType: number
```

表示事件类型。取值为0或1，0表示注视事件，1表示环境音事件。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## fusionReminderData

```TypeScript
fusionReminderData: ReminderLevel
```

表示综合检测后的提醒级别。

**类型：** [ReminderLevel](arkts-multimodalawareness-userstatus-reminderlevel-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。

## swingReminderData

```TypeScript
swingReminderData: ReminderLevel
```

表示注视屏幕时提醒级别。

**类型：** [ReminderLevel](arkts-multimodalawareness-userstatus-reminderlevel-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.UserStatus

**系统接口：** 此接口为系统接口。
