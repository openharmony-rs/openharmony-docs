# @ohos.reminderAgentManager

本模块提供后台代理提醒的能力，即当应用被冻结或应用退出时，定时提醒功能将被系统服务代理。开发者可以调用本模块接口创建定时提醒，提醒类型支持倒计时、日历、闹钟三种。开发指导请参考
[代理提醒开发指南](../../../../task-management/agent-powered-reminder.md)。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.ReminderAgent

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addExcludeDate](arkts-backgroundtasks-addexcludedate-f.md#addexcludedate-1) | 为指定id的周期性的日历提醒，添加不提醒日期（如每天提醒的日历，设置周二不提醒）。使用Promise异步回调。 |
| [addNotificationSlot](arkts-backgroundtasks-addnotificationslot-f.md#addnotificationslot-1) | 添加通知渠道。使用callback异步回调。 |
| [addNotificationSlot](arkts-backgroundtasks-addnotificationslot-f.md#addnotificationslot-2) | 添加通知渠道。使用Promise异步回调。 |
| [cancelAllReminders](arkts-backgroundtasks-cancelallreminders-f.md#cancelallreminders-1) | 取消当前应用设置的所有代理提醒。使用callback异步回调。 |
| [cancelAllReminders](arkts-backgroundtasks-cancelallreminders-f.md#cancelallreminders-2) | 取消当前应用设置的所有代理提醒。使用Promise异步回调。 |
| [cancelReminder](arkts-backgroundtasks-cancelreminder-f.md#cancelreminder-1) | 取消指定id的代理提醒。使用callback异步回调。 |
| [cancelReminder](arkts-backgroundtasks-cancelreminder-f.md#cancelreminder-2) | 取消指定id的代理提醒。使用Promise异步回调。 |
| [cancelReminderOnDisplay](arkts-backgroundtasks-cancelreminderondisplay-f.md#cancelreminderondisplay-1) | 取消当前通知中心内显示的通知卡片，不取消代理提醒数据。例如：每天重复的提醒，该提醒正在通知中心内显示，该接口将通知从通知中心内取消，并且会按照设定的周期，在第二天再次提醒。 |
| [deleteExcludeDates](arkts-backgroundtasks-deleteexcludedates-f.md#deleteexcludedates-1) | 为指定id的周期性的日历提醒，删除设置的所有不提醒日期。使用Promise异步回调。 |
| [getAllValidReminders](arkts-backgroundtasks-getallvalidreminders-f.md#getallvalidreminders-1) | 获取当前应用设置的所有[有效（未过期）的代理提醒](../../../../task-management/agent-powered-reminder.md#约束与限制)。使用Promise异步回调。该接口调用需要申请ohos.permission.PUBLISH_AGENT_REMINDER权限。 |
| [getExcludeDates](arkts-backgroundtasks-getexcludedates-f.md#getexcludedates-1) | 为指定id的周期性的日历提醒，查询设置的所有不提醒日期。使用Promise异步回调。 |
| [getValidReminders](arkts-backgroundtasks-getvalidreminders-f.md#getvalidreminders-1) | 获取当前应用设置的所有[有效（未过期）的代理提醒](../../../../task-management/agent-powered-reminder.md#约束与限制)。使用callback异步回调。 |
| [getValidReminders](arkts-backgroundtasks-getvalidreminders-f.md#getvalidreminders-2) | 获取当前应用设置的所有[有效（未过期）的代理提醒](../../../../task-management/agent-powered-reminder.md#约束与限制)。使用Promise异步回调。 |
| [publishReminder](arkts-backgroundtasks-publishreminder-f.md#publishreminder-1) | 发布后台代理提醒。使用callback异步回调。@link @ohos.notificationManager:notificationManager.requestEnableNotification(context: UIAbilityContext, callback: AsyncCallback&lt;void&gt;)}&gt; 后调用。&gt; |
| [publishReminder](arkts-backgroundtasks-publishreminder-f.md#publishreminder-2) | 发布后台代理提醒。使用Promise异步回调。@link @ohos.notificationManager:notificationManager.requestEnableNotification(context: UIAbilityContext, callback: AsyncCallback&lt;void&gt;)}&gt; 后调用。&gt; |
| [removeNotificationSlot](arkts-backgroundtasks-removenotificationslot-f.md#removenotificationslot-1) | 删除指定的通知渠道类型，使用callback异步回调。 |
| [removeNotificationSlot](arkts-backgroundtasks-removenotificationslot-f.md#removenotificationslot-2) | 删除指定的通知渠道类型，使用Promise异步回调。 |
| [subscribeReminderState](arkts-backgroundtasks-subscribereminderstate-f.md#subscribereminderstate-1) | 订阅代理提醒状态。使用Promise异步回调。 |
| [unsubscribeReminderState](arkts-backgroundtasks-unsubscribereminderstate-f.md#unsubscribereminderstate-1) | 取消订阅代理提醒状态。使用Promise异步回调。 |
| [updateReminder](arkts-backgroundtasks-updatereminder-f.md#updatereminder-1) | 更新指定id的代理提醒，使用Promise异步回调。仅[有效（未过期）](../../../../task-management/agent-powered-reminder.md#约束与限制)、未显示在通知中心的代理提醒支持更新。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ActionButton](arkts-backgroundtasks-actionbutton-i.md) | 弹出的提醒中按钮的类型和标题。 |
| [LocalDateTime](arkts-backgroundtasks-localdatetime-i.md) | 用于日历类提醒设置时指定时间信息。 |
| [MaxScreenWantAgent](arkts-backgroundtasks-maxscreenwantagent-i.md) | 通知中心弹出提醒时，全屏显示自动拉起目标的ability信息。该接口为预留接口，暂不支持使用。 |
| [ReminderInfo](arkts-backgroundtasks-reminderinfo-i.md) | 代理提醒信息，包含 ReminderRequest 和 ReminderId。 |
| [ReminderRequest](arkts-backgroundtasks-reminderrequest-i.md) | 代理提醒对象，用于设置提醒类型、响铃时长等具体信息。 |
| [ReminderRequestAlarm](arkts-backgroundtasks-reminderrequestalarm-i.md) | ReminderRequestAlarm extends ReminderRequest闹钟实例对象，用于设置提醒的时间。 |
| [ReminderRequestCalendar](arkts-backgroundtasks-reminderrequestcalendar-i.md) | ReminderRequestCalendar extends ReminderRequest日历实例对象，用于设置提醒的时间。 |
| [ReminderRequestTimer](arkts-backgroundtasks-reminderrequesttimer-i.md) | ReminderRequestTimer extends ReminderRequest倒计时实例对象，用于设置提醒的时间。 |
| [ReminderState](arkts-backgroundtasks-reminderstate-i.md) | 代理提醒状态信息。状态信息会在如下两种情况发送通知：1. 用户点击代理提醒的通知按钮时，如果应用进程存在，则会发送用户点击的按钮类型的通知给应用。如果应用未运行，则无法收到通知。2. 由于第1点不能保证应用可以收到通知，因此应用注册新的回调函数时，会将该应用下所有用户点击的按钮类型回调给应用。状态信息最多保存30天，应用注册新的回调函数时或者超过30天未注册回调函数，会删除缓存的状态信息。 |
| [WantAgent](arkts-backgroundtasks-wantagent-i.md) | 跳转目标的ability信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionButton](arkts-backgroundtasks-actionbutton-i-sys.md) | 弹出的提醒中按钮的类型和标题。 |
| [DataShareUpdate](arkts-backgroundtasks-datashareupdate-i-sys.md) | 更新数据库需要的参数信息。数据提供方需要在module.json5中的proxyData节点定义要共享的表的标识，读写权限和基本信息。配置方式请见[数据提供方应用的开发](../../../../database/share-data-by-silent-access-sys.md#数据提供方应用的开发)。 |
| [ReminderRequest](arkts-backgroundtasks-reminderrequest-i-sys.md) | 代理提醒对象，用于设置提醒类型、响铃时长等具体信息。 |
| [ReminderRequestCalendar](arkts-backgroundtasks-reminderrequestcalendar-i-sys.md) | ReminderRequestCalendar extends ReminderRequest日历实例对象，用于设置提醒的时间。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ActionButtonType](arkts-backgroundtasks-actionbuttontype-e.md) | 提醒上的按钮的类型。 |
| [ReminderType](arkts-backgroundtasks-remindertype-e.md) | 提醒的类型。 |
| [RingChannel](arkts-backgroundtasks-ringchannel-e.md) | 自定义提示音的音频播放通道。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionButtonType](arkts-backgroundtasks-actionbuttontype-e-sys.md) | 提醒上的按钮的类型。 |
<!--DelEnd-->

