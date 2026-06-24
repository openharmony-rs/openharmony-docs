# publishReminder

## publishReminder

```TypeScript
function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback<number>): void
```

发布一个后台代理提醒，使用回调的方式实现异步调用，该方法需要申请通知弹窗权限
[Notification.requestEnableNotification](../../apis-na/arkts-apis/arkts-na-notification-requestenablenotification-f.md#requestEnableNotification-1)
后才能调用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** publishReminder(reminderReq:

**需要权限：** ohos.permission.PUBLISH_AGENT_REMINDER

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderReq | ReminderRequest | 是 | 需要发布的提醒实例。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 异步回调，返回当前发布的提醒的id。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
import reminderAgent from '@ohos.reminderAgent';

let timer:reminderAgent.ReminderRequestTimer = {
  reminderType: reminderAgent.ReminderType.REMINDER_TYPE_TIMER,
  triggerTimeInSeconds: 10
}

reminderAgent.publishReminder(timer, (err: BusinessError, reminderId: number) => {
  console.info("callback, reminderId = " + reminderId);
});

```


## publishReminder

```TypeScript
function publishReminder(reminderReq: ReminderRequest): Promise<number>
```

发布一个后台代理提醒，使用Promise方式实现异步调用，该方法需要申请通知弹窗权限
[Notification.requestEnableNotification](../../apis-na/arkts-apis/arkts-na-notification-requestenablenotification-f.md#requestEnableNotification-1)
后才能调用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** publishReminder(reminderReq:

**需要权限：** ohos.permission.PUBLISH_AGENT_REMINDER

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderReq | ReminderRequest | 是 | Indicates the reminder instance to publish. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | reminder id. |

**示例：**

```TypeScript
import reminderAgent from '@ohos.reminderAgent';

let timer:reminderAgent.ReminderRequestTimer = {
  reminderType: reminderAgent.ReminderType.REMINDER_TYPE_TIMER,
  triggerTimeInSeconds: 10
}

reminderAgent.publishReminder(timer).then((reminderId: number) => {
  console.info("promise, reminderId = " + reminderId);
});

```

