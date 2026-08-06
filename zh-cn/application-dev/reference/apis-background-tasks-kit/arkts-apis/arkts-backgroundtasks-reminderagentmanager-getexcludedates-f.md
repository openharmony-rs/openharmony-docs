# getExcludeDates

## getExcludeDates

```TypeScript
function getExcludeDates(reminderId: int): Promise<Array<Date>>
```

为指定id的周期性的日历提醒，查询设置的所有不提醒日期。使用Promise异步回调。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-reminderAgentManager-function getExcludeDates(reminderId: int): Promise<Array<Date>>--><!--Device-reminderAgentManager-function getExcludeDates(reminderId: int): Promise<Array<Date>>-End-->

**系统能力：** SystemCapability.Notification.ReminderAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reminderId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 需要查询不提醒日期的代理提醒id。代理提醒id会在[发布代理提醒]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_时作为返回值返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Date&gt;&gt; | Promise对象。返回特定日历设置的所有不提醒日期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [1700003](../../apis-backgroundtasks-kit/errorcode-reminderAgentManager.md#1700003-提醒不存在) | The reminder does not exist. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let reminderId: number = 1;
reminderAgentManager.getExcludeDates(reminderId).then((dates) => {
  console.info("getExcludeDates promise length: " + dates.length);
  for (let i = 0; i < dates.length; i++) {
    console.info("getExcludeDates promise date is: " + dates[i].toString());
  }
}).catch((err: BusinessError) => {
  console.error("promise err code:" + err.code + " message:" + err.message);
});
```

ArkTS-Sta示例：

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';

let reminderId: int = 1;
reminderAgentManager.getExcludeDates(reminderId).then((dates: Array<Date>) => {
  console.info(`Succeeded in getting exclude dates, info is ${JSON.stringify(dates)}.`);
}).catch((err): void => {
  console.error(`Failed to get exclude dates. Code is ${err.code}, message is ${err.message}`);
});
```

