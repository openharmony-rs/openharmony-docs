# cancelReminderOnDisplay

## cancelReminderOnDisplay

```TypeScript
function cancelReminderOnDisplay(reminderId: int): Promise<void>
```

取消当前通知中心内显示的通知卡片，不取消代理提醒数据。例如：每天重复的提醒，该提醒正在通知中心内显示，该接口将通知从通知中心内取消，并且会按照设定的周期，在第二天再次提醒。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-reminderAgentManager-function cancelReminderOnDisplay(reminderId: int): Promise<void>--><!--Device-reminderAgentManager-function cancelReminderOnDisplay(reminderId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 需要取消的代理提醒的id。代理提醒id会在[发布代理提醒]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_时作为返回值返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1700003](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700003-提醒不存在) | The reminder does not exist. |
| [1700007](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700007-参数错误) | If the input parameter is not valid parameter. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

let reminderId: number = 1;
reminderAgentManager.cancelReminderOnDisplay(reminderId).then(() => {
  console.info("cancel display reminder  succeed");
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```

ArkTS-Sta示例：

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let reminderId: int = 1;
reminderAgentManager.cancelReminderOnDisplay(reminderId).then(() => {
  console.info("cancel display reminder succeeded");
}).catch((err): void => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```

