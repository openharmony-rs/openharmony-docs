# stopAndClearWorks

## 导入模块

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## stopAndClearWorks

```TypeScript
function stopAndClearWorks(): void
```

停止和取消当前应用所有的延迟任务。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-workScheduler-function stopAndClearWorks(): void--><!--Device-workScheduler-function stopAndClearWorks(): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [9700001](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700001-内存操作失败) | Memory operation failed. |
| [9700002](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;2. Failed to apply for memory. |
| [9700003](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700003-系统服务失败) | System service operation failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { workScheduler } from '@kit.BackgroundTasksKit';

try {
  workScheduler.stopAndClearWorks();
  console.info(`workschedulerLog stopAndClearWorks success`);
} catch (error) {
  console.error(`workschedulerLog stopAndClearWorks failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
}

```

