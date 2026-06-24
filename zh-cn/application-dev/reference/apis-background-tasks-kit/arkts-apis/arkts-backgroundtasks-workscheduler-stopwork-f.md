# stopWork

## stopWork

```TypeScript
function stopWork(work: WorkInfo, needCancel?: boolean): void
```

取消延迟任务。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| work | WorkInfo | 是 | 要停止或移除的延迟任务。 |
| needCancel | boolean | 否 | 是否需要移除任务。<br/>true表示停止并移除，false表示只停止不移除。默认为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameters types; 3. Parameter verification failed. |
| [9700001](../../errorcode-universal.md#9700001-Memory) | Memory operation failed. |
| [9700002](../../errorcode-universal.md#9700002-Failed) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br/>2. Failed to apply for memory. |
| [9700003](../../errorcode-universal.md#9700003-System) | System service operation failed. |
| [9700004](../../errorcode-universal.md#9700004-Check) | Check on workInfo failed. |

**示例：**

```TypeScript
  import { BusinessError } from '@kit.BasicServicesKit';
  import { workScheduler } from '@kit.BackgroundTasksKit';

  let workInfo: workScheduler.WorkInfo = {
      workId: 1,
      batteryStatus:workScheduler.BatteryStatus.BATTERY_STATUS_LOW,
      isRepeat: false,
      isPersisted: true,
      bundleName: "com.example.myapplication",
      abilityName: "MyExtension",
      parameters: {
          mykey0: 1,
          mykey1: "string value",
          mykey2: true,
          mykey3: 1.5
      }
     }
  try{
    workScheduler.stopWork(workInfo, false);
    console.info('workschedulerLog stopWork success');
  } catch (error) {
    console.error(`workschedulerLog stopWork failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
  }

```

