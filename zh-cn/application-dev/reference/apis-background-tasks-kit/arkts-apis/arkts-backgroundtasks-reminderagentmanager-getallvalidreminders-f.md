# getAllValidReminders

## getAllValidReminders

```TypeScript
function getAllValidReminders(): Promise<Array<ReminderInfo>>
```

获取当前应用设置的所有[有效（未过期）的代理提醒](../../../task-management/agent-powered-reminder.md#约束与限制)。使用Promise异步回调。 该接口调用需要申请ohos.permission.PUBLISH_AGENT_REMINDER权限。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-reminderAgentManager-function getAllValidReminders(): Promise<Array<ReminderInfo>>--><!--Device-reminderAgentManager-function getAllValidReminders(): Promise<Array<ReminderInfo>>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[ReminderInfo](arkts-backgroundtasks-reminderagentmanager-reminderinfo-i.md)&gt;&gt; | Promise对象，返回当前应用设置的所有有效（未过期）的代理提醒。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.getAllValidReminders().then((reminders: Array<reminderAgentManager.ReminderInfo>) => {
  console.info(`Succeeded in getting reminder, info is ${JSON.stringify(reminders)}.`);
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```

ArkTS-Sta示例：

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.getAllValidReminders().then((reminders: Array<reminderAgentManager.ReminderInfo>) => {
  console.info(`Succeeded in getting reminder, info is ${JSON.stringify(reminders)}.`);
}).catch((err): void => {
  console.error(`Failed to get reminder. Code is ${err.code}, message is ${err.message}`);
});
```

