# stopAndClearWorks

## stopAndClearWorks

```TypeScript
function stopAndClearWorks(): void
```

停止和取消当前应用所有的延迟任务。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameters types. |
| [9700001](../../errorcode-universal.md#9700001-Memory) | Memory operation failed. |
| [9700002](../../errorcode-universal.md#9700002-Failed) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br/>2. Failed to apply for memory. |
| [9700003](../../errorcode-universal.md#9700003-System) | System service operation failed. |

**示例：**

```TypeScript
  import { BusinessError } from '@kit.BasicServicesKit';
  import { workScheduler } from '@kit.BackgroundTasksKit';

  try{
    workScheduler.stopAndClearWorks();
    console.info(`workschedulerLog stopAndClearWorks success`);
  } catch (error) {
    console.error(`workschedulerLog stopAndClearWorks failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
  }

```

