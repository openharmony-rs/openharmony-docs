# @ohos.reminderAgent

本模块提供后台代理提醒的能力。

开发应用时，开发者可以调用相关接口创建定时提醒，包括倒计时、日历、闹钟这三类提醒类型。使用后台代理提醒能力后，应用被冻结或退出后，计时和弹出提醒的功能将被后台系统服务代理。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [reminderAgentManager:reminderAgentManager](arkts-reminderagentmanager.md#reminderAgentManager)

**系统能力：** SystemCapability.Notification.ReminderAgent

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addNotificationSlot](arkts-backgroundtasks-reminderagent-addnotificationslot-f.md#addNotificationSlot-1) | 添加一个NotificationSlot，使用回调的方式实现异步调用。<br/> |
| [addNotificationSlot](arkts-backgroundtasks-reminderagent-addnotificationslot-f.md#addNotificationSlot-2) | 添加一个NotificationSlot，使用Promise方式实现异步调用。<br/> |
| [cancelAllReminders](arkts-backgroundtasks-reminderagent-cancelallreminders-f.md#cancelAllReminders-1) | 取消当前应用所有的提醒，使用回调的方式实现异步调用。<br/> |
| [cancelAllReminders](arkts-backgroundtasks-reminderagent-cancelallreminders-f.md#cancelAllReminders-2) | 取消当前应用所有的提醒，使用Promise方式实现异步调用。<br/> |
| [cancelReminder](arkts-backgroundtasks-reminderagent-cancelreminder-f.md#cancelReminder-1) | 取消指定id的提醒，使用回调的方式实现异步调用。<br/> |
| [cancelReminder](arkts-backgroundtasks-reminderagent-cancelreminder-f.md#cancelReminder-2) | 取消指定id的提醒，使用Promise方式实现异步调用。<br/> |
| [getValidReminders](arkts-backgroundtasks-reminderagent-getvalidreminders-f.md#getValidReminders-1) | 获取当前应用已设置的所有有效（未过期）的提醒，使用回调的方式实现异步调用。<br/> |
| [getValidReminders](arkts-backgroundtasks-reminderagent-getvalidreminders-f.md#getValidReminders-2) | 获取当前应用已设置的所有有效（未过期）的提醒，使用Promise方式实现异步调用。<br/> |
| [publishReminder](arkts-backgroundtasks-reminderagent-publishreminder-f.md#publishReminder-1) | 发布一个后台代理提醒，使用回调的方式实现异步调用，该方法需要申请通知弹窗权限<br/>[Notification.requestEnableNotification](@ohos.notification:notification.requestEnableNotification(callback: AsyncCallback&lt;void&gt;))<br/>后才能调用。<br/> |
| [publishReminder](arkts-backgroundtasks-reminderagent-publishreminder-f.md#publishReminder-2) | 发布一个后台代理提醒，使用Promise方式实现异步调用，该方法需要申请通知弹窗权限<br/>[Notification.requestEnableNotification](@ohos.notification:notification.requestEnableNotification(callback: AsyncCallback&lt;void&gt;))<br/>后才能调用。<br/> |
| [removeNotificationSlot](arkts-backgroundtasks-reminderagent-removenotificationslot-f.md#removeNotificationSlot-1) | 删除目标NotificationSlot，使用callback方式实现异步调用。<br/> |
| [removeNotificationSlot](arkts-backgroundtasks-reminderagent-removenotificationslot-f.md#removeNotificationSlot-2) | 删除目标NotificationSlot，使用Promise方式实现异步调用。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ActionButton](arkts-backgroundtasks-reminderagent-actionbutton-i.md) | 用于设置弹出的提醒通知信息上显示的按钮类型和标题。<br/> |
| [LocalDateTime](arkts-backgroundtasks-reminderagent-localdatetime-i.md) | 用于日历类提醒设置时指定时间信息。<br/> |
| [MaxScreenWantAgent](arkts-backgroundtasks-reminderagent-maxscreenwantagent-i.md) | 全屏显示提醒到达时自动拉起的目标ability信息，该接口预留。<br/> |
| [ReminderRequest](arkts-backgroundtasks-reminderagent-reminderrequest-i.md) | 提醒实例对象，用于设置提醒类型、响铃时长等具体信息。<br/> |
| [ReminderRequestAlarm](arkts-backgroundtasks-reminderagent-reminderrequestalarm-i.md) | 闹钟实例对象，用于设置提醒的时间。<br/> |
| [ReminderRequestCalendar](arkts-backgroundtasks-reminderagent-reminderrequestcalendar-i.md) | 日历实例对象，用于设置提醒的时间。<br/> |
| [ReminderRequestTimer](arkts-backgroundtasks-reminderagent-reminderrequesttimer-i.md) | 倒计时实例对象，用于设置提醒的时间。<br/> |
| [WantAgent](arkts-backgroundtasks-reminderagent-wantagent-i.md) | 点击提醒通知后跳转的目标ability信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ActionButtonType](arkts-backgroundtasks-reminderagent-actionbuttontype-e.md) | 按钮的类型。<br/> |
| [ReminderType](arkts-backgroundtasks-reminderagent-remindertype-e.md) | 提醒的类型。<br/> |

