# updateReminder

## updateReminder

```TypeScript
function updateReminder(reminderId: number, reminderReq: ReminderRequest): Promise<void>
```

更新指定id的代理提醒，使用Promise异步回调。仅[有效（未过期）](../../../../task-management/agent-powered-reminder.md#约束与限制)、未显示在通知中心的代理提醒支持更新。

**起始版本：** 20

**需要权限：** ohos.permission.PUBLISH_AGENT_REMINDER

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderId | number | 是 | 需要更新的代理提醒的id。代理提醒id会在[发布代理提醒](arkts-backgroundtasks-publishreminder-f.md#publishreminder-1)时作为返回值返回。 |
| reminderReq | ReminderRequest | 是 | 代理提醒对象实例，用于设置提醒类型、响铃时长等具体信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [1700003](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700003-提醒不存在) | The reminder does not exist. |
| [1700007](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700007-参数错误) | If the input parameter is not valid parameter. |

**示例：**

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

let timer: reminderAgentManager.ReminderRequestTimer = {
  reminderType: reminderAgentManager.ReminderType.REMINDER_TYPE_TIMER,
  triggerTimeInSeconds: 10
}

let reminderId: number = 1;
reminderAgentManager.updateReminder(reminderId, timer).then(() => {
  console.info("update reminder succeed");
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});

```

