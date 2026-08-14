# cancelAllReminders

## cancelAllReminders

```TypeScript
function cancelAllReminders(callback: AsyncCallback<void>): void
```

取消当前应用设置的所有代理提醒。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-reminderAgentManager-function cancelAllReminders(callback: AsyncCallback<void>): void--><!--Device-reminderAgentManager-function cancelAllReminders(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。 当取消代理提醒成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter is not valid parameter. |
| [1700004](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700004-包名不存在) | The bundle name does not exist. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.cancelAllReminders((err: BusinessError) =>{
  if (err.code) {
    console.error("callback err code:" + err.code + " message:" + err.message);
  } else {
    console.info("cancelAllReminders callback")
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let cancelCallback = (err: BusinessError | null) => {
  if (err) {
    console.error(`Failed to cancel all reminder. Code is ${err.code}, message is ${err.message}`);
  } else {
    console.info(`Succeeded in canceling all reminders.`);
  }
}

reminderAgentManager.cancelAllReminders(cancelCallback);
```


## cancelAllReminders

```TypeScript
function cancelAllReminders(): Promise<void>
```

取消当前应用设置的所有代理提醒。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-reminderAgentManager-function cancelAllReminders(): Promise<void>--><!--Device-reminderAgentManager-function cancelAllReminders(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter is not valid parameter. |
| [1700004](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700004-包名不存在) | The bundle name does not exist. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.cancelAllReminders().then(() => {
  console.info("cancelAllReminders promise")
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```

ArkTS-Sta示例：

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

reminderAgentManager.cancelAllReminders().then(() => {
  console.info(`Succeeded in canceling all reminders.`);
}).catch((err): void => {
  console.error(`Failed to cancel all reminder. Code is ${err.code}, message is ${err.message}`);
});
```

