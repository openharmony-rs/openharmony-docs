# publishReminder

## publishReminder

```TypeScript
function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback<number>): void
```

发布后台代理提醒。使用callback异步回调。

> **说明：**
>
> 该接口需要申请通知弹窗权限
> [notificationManager.requestEnableNotification](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-requestenablenotification-f.md#requestEnableNotification-2)
> 后调用。
>

**起始版本：** 9

**需要权限：** ohos.permission.PUBLISH_AGENT_REMINDER

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderReq | ReminderRequest | 是 | 需要发布的代理提醒实例。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 回调函数。<br/>当代理提醒发布成功，err为undefined，data为当前发布提醒的id；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-If) | If the input parameter is not valid parameter. |
| [1700001](../../errorcode-universal.md#1700001-Notification) | Notification is not enabled. |
| [1700002](../../errorcode-universal.md#1700002-The) | The number of reminders exceeds the limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let timer: reminderAgentManager.ReminderRequestTimer = {
  reminderType: reminderAgentManager.ReminderType.REMINDER_TYPE_TIMER,
  triggerTimeInSeconds: 10
}

reminderAgentManager.publishReminder(timer, (err: BusinessError, reminderId: number) => {
  if (err.code) {
    console.error("callback err code:" + err.code + " message:" + err.message);
  } else {
    console.info("callback, reminderId = " + reminderId);
  }
});

```


## publishReminder

```TypeScript
function publishReminder(reminderReq: ReminderRequest): Promise<number>
```

发布后台代理提醒。使用Promise异步回调。

> **说明：**
>
> 该接口需要申请通知弹窗权限
> [notificationManager.requestEnableNotification](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-requestenablenotification-f.md#requestEnableNotification-2)
> 后调用。
>

**起始版本：** 9

**需要权限：** ohos.permission.PUBLISH_AGENT_REMINDER

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderReq | ReminderRequest | 是 | 需要发布的代理提醒实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回当前发布提醒的id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-If) | If the input parameter is not valid parameter. |
| [1700001](../../errorcode-universal.md#1700001-Notification) | Notification is not enabled. |
| [1700002](../../errorcode-universal.md#1700002-The) | The number of reminders exceeds the limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let timer: reminderAgentManager.ReminderRequestTimer = {
  reminderType: reminderAgentManager.ReminderType.REMINDER_TYPE_TIMER,
  triggerTimeInSeconds: 10
}

reminderAgentManager.publishReminder(timer).then((reminderId: number) => {
  console.info("promise, reminderId = " + reminderId);
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});

```

