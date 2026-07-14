# @ohos.reminderAgent

本模块提供后台代理提醒的能力。

开发应用时，开发者可以调用相关接口创建定时提醒，包括倒计时、日历、闹钟这三类提醒类型。使用后台代理提醒能力后，应用被冻结或退出后，计时和弹出提醒的功能将被后台系统服务代理。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [reminderAgentManager:reminderAgentManager](arkts-reminderagentmanager.md)

**系统能力：** SystemCapability.Notification.ReminderAgent

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addNotificationSlot](arkts-backgroundtasks-addnotificationslot-f.md#addnotificationslot-1) | 添加一个NotificationSlot，使用回调的方式实现异步调用。 |
| [addNotificationSlot](arkts-backgroundtasks-addnotificationslot-f.md#addnotificationslot-2) | 添加一个NotificationSlot，使用Promise方式实现异步调用。 |
| [cancelAllReminders](arkts-backgroundtasks-cancelallreminders-f.md#cancelallreminders-1) | 取消当前应用所有的提醒，使用回调的方式实现异步调用。 |
| [cancelAllReminders](arkts-backgroundtasks-cancelallreminders-f.md#cancelallreminders-2) | 取消当前应用所有的提醒，使用Promise方式实现异步调用。 |
| [cancelReminder](arkts-backgroundtasks-cancelreminder-f.md#cancelreminder-1) | 取消指定id的提醒，使用回调的方式实现异步调用。 |
| [cancelReminder](arkts-backgroundtasks-cancelreminder-f.md#cancelreminder-2) | 取消指定id的提醒，使用Promise方式实现异步调用。 |
| [getValidReminders](arkts-backgroundtasks-getvalidreminders-f.md#getvalidreminders-1) | 获取当前应用已设置的所有有效（未过期）的提醒，使用回调的方式实现异步调用。 |
| [getValidReminders](arkts-backgroundtasks-getvalidreminders-f.md#getvalidreminders-2) | 获取当前应用已设置的所有有效（未过期）的提醒，使用Promise方式实现异步调用。 |
| [publishReminder](arkts-backgroundtasks-publishreminder-f.md#publishreminder-1) | 发布一个后台代理提醒，使用回调的方式实现异步调用，该方法需要申请通知弹窗权限[Notification.requestEnableNotification](../../apis-notification-kit/arkts-apis/arkts-notification-requestenablenotification-depr-f.md#requestenablenotification-1)后才能调用。 |
| [publishReminder](arkts-backgroundtasks-publishreminder-f.md#publishreminder-2) | 发布一个后台代理提醒，使用Promise方式实现异步调用，该方法需要申请通知弹窗权限[Notification.requestEnableNotification](../../apis-notification-kit/arkts-apis/arkts-notification-requestenablenotification-depr-f.md#requestenablenotification-1)后才能调用。 |
| [removeNotificationSlot](arkts-backgroundtasks-removenotificationslot-f.md#removenotificationslot-1) | 删除目标NotificationSlot，使用callback方式实现异步调用。 |
| [removeNotificationSlot](arkts-backgroundtasks-removenotificationslot-f.md#removenotificationslot-2) | 删除目标NotificationSlot，使用Promise方式实现异步调用。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ActionButton](arkts-backgroundtasks-actionbutton-i.md) | 用于设置弹出的提醒通知信息上显示的按钮类型和标题。 |
| [LocalDateTime](arkts-backgroundtasks-localdatetime-i.md) | 用于日历类提醒设置时指定时间信息。 |
| [MaxScreenWantAgent](arkts-backgroundtasks-maxscreenwantagent-i.md) | 全屏显示提醒到达时自动拉起的目标ability信息，该接口预留。 |
| [ReminderRequest](arkts-backgroundtasks-reminderrequest-i.md) | 提醒实例对象，用于设置提醒类型、响铃时长等具体信息。 |
| [ReminderRequestAlarm](arkts-backgroundtasks-reminderrequestalarm-i.md) | 闹钟实例对象，用于设置提醒的时间。 |
| [ReminderRequestCalendar](arkts-backgroundtasks-reminderrequestcalendar-i.md) | 日历实例对象，用于设置提醒的时间。 |
| [ReminderRequestTimer](arkts-backgroundtasks-reminderrequesttimer-i.md) | 倒计时实例对象，用于设置提醒的时间。 |
| [WantAgent](arkts-backgroundtasks-wantagent-i.md) | 点击提醒通知后跳转的目标ability信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ActionButtonType](arkts-backgroundtasks-actionbuttontype-e.md) | 按钮的类型。 |
| [ReminderType](arkts-backgroundtasks-remindertype-e.md) | 提醒的类型。 |

