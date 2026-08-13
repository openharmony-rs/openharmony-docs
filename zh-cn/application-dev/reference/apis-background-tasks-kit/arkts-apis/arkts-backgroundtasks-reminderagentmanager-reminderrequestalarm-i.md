# ReminderRequestAlarm

ReminderRequestAlarm extends ReminderRequest 闹钟实例对象，用于设置提醒的时间。

**继承/实现关系：** ReminderRequestAlarm extends [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md#ReminderRequest)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-reminderAgentManager-interface ReminderRequestAlarm--><!--Device-reminderAgentManager-interface ReminderRequestAlarm-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## daysOfWeek

```TypeScript
daysOfWeek?: Array<int>
```

指明每周哪几天需要重复提醒。范围为周一到周日，对应数字为1到7，默认为空。

**类型：** Array&lt;int&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequestAlarm-daysOfWeek?: Array<int>--><!--Device-ReminderRequestAlarm-daysOfWeek?: Array<int>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## hour

```TypeScript
hour: int
```

指明提醒的目标时刻，范围：[0, 23]。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequestAlarm-hour: int--><!--Device-ReminderRequestAlarm-hour: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

## minute

```TypeScript
minute: int
```

指明提醒的目标分钟，范围：[0, 59]。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ReminderRequestAlarm-minute: int--><!--Device-ReminderRequestAlarm-minute: int-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

