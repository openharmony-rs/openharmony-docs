# addExcludeDate

## addExcludeDate

```TypeScript
function addExcludeDate(reminderId: number, date: Date): Promise<void>
```

为指定id的周期性的日历提醒，添加不提醒日期（如每天提醒的日历，设置周二不提醒）。使用Promise异步回调。

**起始版本：** 12

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderId | number | 是 | 需要添加不提醒日期的代理提醒id。<br/>代理提醒id会在<br/>[发布代理提醒](arkts-backgroundtasks-reminderagentmanager-publishreminder-f.md#publishReminder-1)<br/>时作为返回值返回。 |
| date | Date | 是 | 不提醒的日期。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied |
| [401](../../errorcode-universal.md#401-If) | If the input parameter is not valid parameter. |
| [1700003](../../errorcode-universal.md#1700003-The) | The reminder does not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let reminderId: number = 1;
let date = new Date();
reminderAgentManager.addExcludeDate(reminderId, date).then(() => {
  console.info("addExcludeDate promise");
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});

```

