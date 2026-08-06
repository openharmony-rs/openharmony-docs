# updateReminder

## updateReminder

```TypeScript
function updateReminder(reminderId: int, reminderReq: ReminderRequest): Promise<void>
```

更新指定id的代理提醒，使用Promise异步回调。仅\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_、未显示在通知中心的代理提醒支持更新。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.PUBLISH_AGENT_REMINDER

<!--Device-reminderAgentManager-function updateReminder(reminderId: int, reminderReq: ReminderRequest): Promise<void>--><!--Device-reminderAgentManager-function updateReminder(reminderId: int, reminderReq: ReminderRequest): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 需要更新的代理提醒的id。代理提醒id会在[发布代理提醒]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_时作为返回值返回。 |
| reminderReq | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 代理提醒对象实例，用于设置提醒类型、响铃时长等具体信息。 |

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

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let timer: reminderAgentManager.ReminderRequestTimer = {
  reminderType: reminderAgentManager.ReminderType.REMINDER_TYPE_TIMER,
  triggerTimeInSeconds: 10
}

let reminderId: int = 1;
reminderAgentManager.updateReminder(reminderId, timer).then(() => {
  console.info(`Succeeded in updating reminder.`);
}).catch((err): void => {
  console.error(`Failed to update reminder. Code is ${err.code}, message is ${err.message}`);
});
```

