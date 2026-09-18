# @ohos.reminderAgentManager(后台代理提醒)

本模块提供后台代理提醒的能力，即当应用被冻结或应用退出时，定时提醒功能将被系统服务代理。开发者可以调用本模块接口创建定时提醒，提醒类型支持倒计时、日历、闹钟三种。开发指导请参考[代理提醒开发指南](../../../task-management/agent-powered-reminder.md)。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addExcludeDate](arkts-backgroundtasks-reminderagentmanager-addexcludedate-f.md) | 为指定id的周期性的日历提醒，添加不提醒日期（如每天提醒的日历，设置周二不提醒）。使用Promise异步回调。 |
| [addNotificationSlot](arkts-backgroundtasks-reminderagentmanager-addnotificationslot-f.md) | 添加通知渠道。使用callback异步回调。 |
| [addNotificationSlot](arkts-backgroundtasks-reminderagentmanager-addnotificationslot-f.md) | 添加通知渠道。使用Promise异步回调。 |
| [cancelAllReminders](arkts-backgroundtasks-reminderagentmanager-cancelallreminders-f.md) | 取消当前应用设置的所有代理提醒。使用callback异步回调。 |
| [cancelAllReminders](arkts-backgroundtasks-reminderagentmanager-cancelallreminders-f.md) | 取消当前应用设置的所有代理提醒。使用Promise异步回调。 |
| [cancelReminder](arkts-backgroundtasks-reminderagentmanager-cancelreminder-f.md) | 取消指定id的代理提醒。使用callback异步回调。 |
| [cancelReminder](arkts-backgroundtasks-reminderagentmanager-cancelreminder-f.md) | 取消指定id的代理提醒。使用Promise异步回调。 |
| [cancelReminderOnDisplay](arkts-backgroundtasks-reminderagentmanager-cancelreminderondisplay-f.md) | 取消当前通知中心内显示的通知卡片，不取消代理提醒数据。例如：每天重复的提醒，该提醒正在通知中心内显示，该接口将通知从通知中心内取消，并且会按照设定的周期，在第二天再次提醒。 |
| [deleteExcludeDates](arkts-backgroundtasks-reminderagentmanager-deleteexcludedates-f.md) | 为指定id的周期性的日历提醒，删除设置的所有不提醒日期。使用Promise异步回调。 |
| [getAllValidReminders](arkts-backgroundtasks-reminderagentmanager-getallvalidreminders-f.md) | 获取当前应用设置的所有[有效（未过期）的代理提醒](../../../task-management/agent-powered-reminder.md#约束与限制)。使用Promise异步回调。该接口调用需要申请ohos.permission.PUBLISH_AGENT_REMINDER权限。 |
| [getExcludeDates](arkts-backgroundtasks-reminderagentmanager-getexcludedates-f.md) | 为指定id的周期性的日历提醒，查询设置的所有不提醒日期。使用Promise异步回调。 |
| [getValidReminders](arkts-backgroundtasks-reminderagentmanager-getvalidreminders-f.md) | 获取当前应用设置的所有[有效（未过期）的代理提醒](../../../task-management/agent-powered-reminder.md#约束与限制)。使用callback异步回调。 |
| [getValidReminders](arkts-backgroundtasks-reminderagentmanager-getvalidreminders-f.md) | 获取当前应用设置的所有[有效（未过期）的代理提醒](../../../task-management/agent-powered-reminder.md#约束与限制)。使用Promise异步回调。 |
| [publishReminder](arkts-backgroundtasks-reminderagentmanager-publishreminder-f.md) | 发布后台代理提醒。使用callback异步回调。 |
| [publishReminder](arkts-backgroundtasks-reminderagentmanager-publishreminder-f.md) | 发布后台代理提醒。使用Promise异步回调。 |
| [removeNotificationSlot](arkts-backgroundtasks-reminderagentmanager-removenotificationslot-f.md) | 删除指定的通知渠道类型，使用callback异步回调。 |
| [removeNotificationSlot](arkts-backgroundtasks-reminderagentmanager-removenotificationslot-f.md) | 删除指定的通知渠道类型，使用Promise异步回调。 |
| [subscribeReminderState](arkts-backgroundtasks-reminderagentmanager-subscribereminderstate-f.md) | 订阅代理提醒状态。使用Promise异步回调。 |
| [unsubscribeReminderState](arkts-backgroundtasks-reminderagentmanager-unsubscribereminderstate-f.md) | 取消订阅代理提醒状态。使用Promise异步回调。 |
| [updateReminder](arkts-backgroundtasks-reminderagentmanager-updatereminder-f.md) | 更新指定id的代理提醒，使用Promise异步回调。仅[有效（未过期）](../../../task-management/agent-powered-reminder.md#约束与限制)、未显示在通知中心的代理提醒支持更新。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ActionButton](arkts-backgroundtasks-reminderagentmanager-actionbutton-i.md) | 弹出的提醒中按钮的类型和标题。 |
| [LocalDateTime](arkts-backgroundtasks-reminderagentmanager-localdatetime-i.md) | 用于日历类提醒设置时指定时间信息。 |
| [MaxScreenWantAgent](arkts-backgroundtasks-reminderagentmanager-maxscreenwantagent-i.md) | 通知中心弹出提醒时，全屏显示自动拉起目标的ability信息。该接口为预留接口，暂不支持使用。 |
| [NotificationRequestProxy](arkts-backgroundtasks-reminderagentmanager-notificationrequestproxy-i.md) | 通知请求信息。 |
| [ReminderInfo](arkts-backgroundtasks-reminderagentmanager-reminderinfo-i.md) | 代理提醒信息，包含 ReminderRequest 和 ReminderId。 |
| [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md) | 代理提醒对象，用于设置提醒类型、响铃时长等具体信息。 |
| [ReminderRequestAlarm](arkts-backgroundtasks-reminderagentmanager-reminderrequestalarm-i.md) | ReminderRequestAlarm extends ReminderRequest |
| [ReminderRequestCalendar](arkts-backgroundtasks-reminderagentmanager-reminderrequestcalendar-i.md) | ReminderRequestCalendar extends ReminderRequest |
| [ReminderRequestTimer](arkts-backgroundtasks-reminderagentmanager-reminderrequesttimer-i.md) | ReminderRequestTimer extends ReminderRequest |
| [ReminderState](arkts-backgroundtasks-reminderagentmanager-reminderstate-i.md) | 代理提醒状态信息。状态信息会在如下两种情况发送通知： |
| [WantAgent](arkts-backgroundtasks-reminderagentmanager-wantagent-i.md) | 跳转目标的ability信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionButton](arkts-backgroundtasks-reminderagentmanager-actionbutton-i-sys.md) | 弹出的提醒中按钮的类型和标题。 |
| [DataShareUpdate](arkts-backgroundtasks-reminderagentmanager-datashareupdate-i-sys.md) | 更新数据库需要的参数信息。 |
| [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i-sys.md) | 代理提醒对象，用于设置提醒类型、响铃时长等具体信息。 |
| [ReminderRequestCalendar](arkts-backgroundtasks-reminderagentmanager-reminderrequestcalendar-i-sys.md) | ReminderRequestCalendar extends ReminderRequest |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ActionButtonType](arkts-backgroundtasks-reminderagentmanager-actionbuttontype-e.md) | 提醒上的按钮的类型。 |
| [ReminderType](arkts-backgroundtasks-reminderagentmanager-remindertype-e.md) | 提醒的类型。 |
| [RingChannel](arkts-backgroundtasks-reminderagentmanager-ringchannel-e.md) | 自定义提示音的音频播放通道。 |
| [TimeZoneType](arkts-backgroundtasks-reminderagentmanager-timezonetype-e.md) | 时区类型。用于时区变更时，按照变更后的时区重新计算提醒的目标时间。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionButtonType](arkts-backgroundtasks-reminderagentmanager-actionbuttontype-e-sys.md) | 提醒上的按钮的类型。 |
<!--DelEnd-->
