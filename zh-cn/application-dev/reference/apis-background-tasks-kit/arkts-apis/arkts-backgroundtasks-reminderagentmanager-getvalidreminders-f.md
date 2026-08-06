# getValidReminders

## getValidReminders

```TypeScript
function getValidReminders(callback: AsyncCallback<Array<ReminderRequest>>): void
```

获取当前应用设置的所有\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-reminderAgentManager-function getValidReminders(callback: AsyncCallback<Array<ReminderRequest>>): void--><!--Device-reminderAgentManager-function getValidReminders(callback: AsyncCallback<Array<ReminderRequest>>): void-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;ReminderRequest&gt;&gt; | 是 | 回调函数。当查询代理提醒成功，err为undefined，data为当前应用设置的所有有效（未过期）的代理提醒；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter is not valid parameter. |
| [1700004](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700004-包名不存在) | The bundle name does not exist. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.getValidReminders((err: BusinessError, reminders: Array<reminderAgentManager.ReminderRequest>) => {
  if (err.code) {
    console.error("callback err code:" + err.code + " message:" + err.message);
  } else {
    console.info(`Succeeded in getting reminder, info is ${JSON.stringify(reminders)}.`);
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let getCallback = (err: BusinessError | null, reminders: Array<reminderAgentManager.ReminderRequest> | undefined | null) => {
  if (err) {
    console.error(`Failed to get reminder. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in getting reminder, info is ${JSON.stringify(reminders)}.`);
  }
}

reminderAgentManager.getValidReminders(getCallback);
```


## getValidReminders

```TypeScript
function getValidReminders(): Promise<Array<ReminderRequest>>
```

获取当前应用设置的所有\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-reminderAgentManager-function getValidReminders(): Promise<Array<ReminderRequest>>--><!--Device-reminderAgentManager-function getValidReminders(): Promise<Array<ReminderRequest>>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ReminderRequest&gt;&gt; | Promise对象，返回当前应用设置的所有有效（未过期）的代理提醒。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter is not valid parameter. |
| [1700004](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700004-包名不存在) | The bundle name does not exist. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.getValidReminders().then((reminders: Array<reminderAgentManager.ReminderRequest>) => {
  console.info(`Succeeded in getting reminder, info is ${JSON.stringify(reminders)}.`);
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```

ArkTS-Sta示例：

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.getValidReminders().then((reminders: Array<reminderAgentManager.ReminderRequest>) => {
  console.info(`Succeeded in getting reminder, info is ${JSON.stringify(reminders)}.`);
}).catch((err): void => {
  console.error(`Failed to get reminder. Code is ${err.code}, message is ${err.message}`);
});
```

