# subscribeReminderState

## 导入模块

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

<a id="subscribereminderstate"></a>
## subscribeReminderState

```TypeScript
function subscribeReminderState(callback: Callback<Array<ReminderState>>): Promise<void>
```

订阅代理提醒状态。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.PUBLISH_AGENT_REMINDER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-reminderAgentManager-function subscribeReminderState(callback: Callback<Array<ReminderState>>): Promise<void>--><!--Device-reminderAgentManager-function subscribeReminderState(callback: Callback<Array<ReminderState>>): Promise<void>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Array&lt;ReminderState&gt;&gt; | 是 | 回调函数，返回代理提醒状态信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [1700007](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700007-参数错误) | If the input parameter is not valid parameter. |

**示例：**

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

function reminderStateCallback(states: Array<reminderAgentManager.ReminderState>) {
  console.info('length is : ' + states.length);
}

reminderAgentManager.subscribeReminderState(reminderStateCallback).then(() => {
  console.info('subscribe succeed');
}).catch((err: BusinessError) => {
  console.error('promise err code:' + err.code + ' message:' + err.message);
});

```

