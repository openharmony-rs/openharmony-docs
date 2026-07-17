# ReminderState

代理提醒状态信息。状态信息会在如下两种情况发送通知：

1. 用户点击代理提醒的通知按钮时，如果应用进程存在，则会发送用户点击的按钮类型的通知给应用。如果应用未运行，则无法收到通知。2. 由于第1点不能保证应用可以收到通知，因此应用注册新的回调函数时，会将该应用下所有用户点击的按钮类型回调给应用。状态信息最多保存30天，应用注册新的回调函数时或者超过30天未注册回调函数，会删除缓存的状态信息。

**起始版本：** 23

<!--Device-reminderAgentManager-interface ReminderState--><!--Device-reminderAgentManager-interface ReminderState-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## buttonType

```TypeScript
buttonType: ActionButtonType
```

按钮类型。

**类型：** ActionButtonType

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReminderState-buttonType: ActionButtonType--><!--Device-ReminderState-buttonType: ActionButtonType-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## isMessageResent

```TypeScript
isMessageResent: boolean
```

信息是否为重复发送。

- false：信息首次发送。具体场景包括：用户点击代理提醒的通知按钮时，应用进程存在；用户点击代理提醒的通知按钮时，应用未运行，后续应用注册新的回调函数。  
- true：信息重复发送，具体场景为：应用进程存在，用户点击代理提醒的通知按钮后，应用注册新的回调函数。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReminderState-isMessageResent: boolean--><!--Device-ReminderState-isMessageResent: boolean-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## reminderId

```TypeScript
reminderId: number
```

发布提醒后返回的id。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ReminderState-reminderId: int--><!--Device-ReminderState-reminderId: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

