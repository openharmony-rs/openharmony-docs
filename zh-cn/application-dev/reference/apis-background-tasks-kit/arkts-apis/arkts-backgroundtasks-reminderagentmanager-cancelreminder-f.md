# cancelReminder

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

<a id="cancelreminder"></a>
## cancelReminder

```TypeScript
function cancelReminder(reminderId: number, callback: AsyncCallback<void>): void
```

取消指定id的代理提醒。使用callback异步回调。

**起始版本：** 9

<!--Device-reminderAgentManager-function cancelReminder(reminderId: int, callback: AsyncCallback<void>): void--><!--Device-reminderAgentManager-function cancelReminder(reminderId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderId | number | 是 | 需要取消的代理提醒的id。代理提醒id会在[发布代理提醒](arkts-backgroundtasks-reminderagentmanager-publishreminder-f.md#publishreminder-1)时作为返回值返回。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当取消代理提醒成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter is not valid parameter. |
| [1700003](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700003-提醒不存在) | The reminder does not exist. |
| [1700004](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700004-包名不存在) | The bundle name does not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let reminderId: number = 1;
reminderAgentManager.cancelReminder(reminderId, (err: BusinessError) => {
  if (err.code) {
    console.error("callback err code:" + err.code + " message:" + err.message);
  } else {
    console.info("cancelReminder callback");
  }
});

```


<a id="cancelreminder-1"></a>
## cancelReminder

```TypeScript
function cancelReminder(reminderId: number): Promise<void>
```

取消指定id的代理提醒。使用Promise异步回调。

**起始版本：** 9

<!--Device-reminderAgentManager-function cancelReminder(reminderId: int): Promise<void>--><!--Device-reminderAgentManager-function cancelReminder(reminderId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderId | number | 是 | 需要取消的代理提醒的id。代理提醒id会在[发布代理提醒](arkts-backgroundtasks-reminderagentmanager-publishreminder-f.md#publishreminder-1)时作为返回值返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter is not valid parameter. |
| [1700003](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700003-提醒不存在) | The reminder does not exist. |
| [1700004](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700004-包名不存在) | The bundle name does not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let reminderId: number = 1;
reminderAgentManager.cancelReminder(reminderId).then(() => {
  console.info("cancelReminder promise");
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});

```

