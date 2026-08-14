# publishReminder

## publishReminder

```TypeScript
function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback<int>): void
```

发布后台代理提醒。使用callback异步回调。 > **说明：** > > 该接口需要申请通知弹窗权限 > [notificationManager.requestEnableNotification](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-requestenablenotification-f.md#requestEnableNotification) > 后调用。 >

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PUBLISH_AGENT_REMINDER

<!--Device-reminderAgentManager-function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback<int>): void--><!--Device-reminderAgentManager-function publishReminder(reminderReq: ReminderRequest, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderReq | ReminderRequest | 是 | 需要发布的代理提醒实例。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数。 当代理提醒发布成功，err为undefined，data为当前发布提醒的id；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter is not valid parameter. |
| [1700001](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700001-通知使能未开启) | Notification is not enabled. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [1700002](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700002-提醒数量超出限制) | The number of reminders exceeds the limit. |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

// publishReminder回调
let publishCallback = (err: BusinessError | null, reminderId: int | undefined | null): void => {
  if (err) {
    console.error(`Failed to publish reminder. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in publishing reminder, id is ${JSON.stringify(reminderId)}.`);
  }
}

let timer: reminderAgentManager.ReminderRequestTimer = {
  reminderType: reminderAgentManager.ReminderType.REMINDER_TYPE_TIMER,
  triggerTimeInSeconds: 10
}

reminderAgentManager.publishReminder(timer, publishCallback);
```


## publishReminder

```TypeScript
function publishReminder(reminderReq: ReminderRequest): Promise<int>
```

发布后台代理提醒。使用Promise异步回调。 > **说明：** > > 该接口需要申请通知弹窗权限 > [notificationManager.requestEnableNotification](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager-requestenablenotification-f.md#requestEnableNotification) > 后调用。 >

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PUBLISH_AGENT_REMINDER

<!--Device-reminderAgentManager-function publishReminder(reminderReq: ReminderRequest): Promise<int>--><!--Device-reminderAgentManager-function publishReminder(reminderReq: ReminderRequest): Promise<int>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderReq | ReminderRequest | 是 | 需要发布的代理提醒实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回当前发布提醒的id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter is not valid parameter. |
| [1700001](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700001-通知使能未开启) | Notification is not enabled. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [1700002](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700002-提醒数量超出限制) | The number of reminders exceeds the limit. |

## 示例

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let timer: reminderAgentManager.ReminderRequestTimer = {
  reminderType: reminderAgentManager.ReminderType.REMINDER_TYPE_TIMER,
  triggerTimeInSeconds: 10
}

reminderAgentManager.publishReminder(timer).then((reminderId: int) => {
  console.info(`Succeeded in publishing reminder, reminderId is  ${JSON.stringify(reminderId)}.`);
}).catch((err): void => {
  console.error(`Failed to publish reminder. Code is ${err.code}, message is ${err.message}`);
});
```

