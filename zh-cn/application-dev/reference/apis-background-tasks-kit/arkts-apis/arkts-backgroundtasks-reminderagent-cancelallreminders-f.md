# cancelAllReminders

## cancelAllReminders

```TypeScript
function cancelAllReminders(callback: AsyncCallback<void>): void
```

取消当前应用所有的提醒，使用回调的方式实现异步调用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [reminderAgentManager.cancelAllReminders](arkts-backgroundtasks-reminderagentmanager-cancelallreminders-f.md#cancelallreminders)

<!--Device-reminderAgent-function cancelAllReminders(callback: AsyncCallback<void>): void--><!--Device-reminderAgent-function cancelAllReminders(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 异步回调。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
import reminderAgent from '@ohos.reminderAgent';

reminderAgent.cancelAllReminders((err: BusinessError, data: void) =>{
  console.info("cancelAllReminders callback")
})
```


## cancelAllReminders

```TypeScript
function cancelAllReminders(): Promise<void>
```

取消当前应用所有的提醒，使用Promise方式实现异步调用。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [reminderAgentManager.cancelAllReminders](arkts-backgroundtasks-reminderagentmanager-cancelallreminders-f.md#cancelallreminders)

<!--Device-reminderAgent-function cancelAllReminders(): Promise<void>--><!--Device-reminderAgent-function cancelAllReminders(): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise类型异步回调。 |

**示例：**

```TypeScript
import reminderAgent from '@ohos.reminderAgent';

reminderAgent.cancelAllReminders().then(() => {
    console.info("cancelAllReminders promise")
})
```

