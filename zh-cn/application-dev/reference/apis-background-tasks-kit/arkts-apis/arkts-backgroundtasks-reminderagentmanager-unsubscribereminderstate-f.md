# unsubscribeReminderState

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

<a id="unsubscribereminderstate"></a>
## unsubscribeReminderState

```TypeScript
function unsubscribeReminderState(callback?: Callback<Array<ReminderState>>): Promise<void>
```

取消订阅代理提醒状态。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-reminderAgentManager-function unsubscribeReminderState(callback?: Callback<Array<ReminderState>>): Promise<void>--><!--Device-reminderAgentManager-function unsubscribeReminderState(callback?: Callback<Array<ReminderState>>): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Array&lt;ReminderState&gt;&gt; | 否 | 回调函数。如果不传参数callback，则取消所有订阅。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1700007](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700007-参数错误) | If the input parameter is not valid parameter. |

**示例：**

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

function reminderStateCallback(states: Array<reminderAgentManager.ReminderState>) {
  console.info('length is : ' + states.length);
}

reminderAgentManager.unsubscribeReminderState(reminderStateCallback).then(() => {
  console.info('unsubscribe succeed');
}).catch((err: BusinessError) => {
  console.error('promise err code:' + err.code + ' message:' + err.message);
});

```

