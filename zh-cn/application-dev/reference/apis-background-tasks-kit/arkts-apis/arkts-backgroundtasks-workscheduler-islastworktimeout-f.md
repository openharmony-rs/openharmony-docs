# isLastWorkTimeOut

## isLastWorkTimeOut

```TypeScript
function isLastWorkTimeOut(workId: number, callback: AsyncCallback<void>): boolean
```

检查延迟任务的最后一次执行是否超时，使用Callback异步回调。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 10

**替代接口：** [isLastWorkTimeOut](#isLastWorkTimeOut)(workId: int, callback: AsyncCallback&lt;boolean&gt;)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-workScheduler-function isLastWorkTimeOut(workId: number, callback: AsyncCallback<void>): boolean--><!--Device-workScheduler-function isLastWorkTimeOut(workId: number, callback: AsyncCallback<void>): boolean-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| workId | number | 是 | 指定延迟任务的Id。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查延迟任务最后一次执行是否超时，如果workId有效，则返回从WorkSchedulerService获取的任务最后一次执行是否超时；否则，抛出异常。true，对应workId延迟任务最 后一次执行超时，false，对应workId延迟任务最后一次执行未超时。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9700004](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700004-workinfo校验失败) | Check on workInfo failed. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: Parameter verification failed. |
| [9700001](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700001-内存操作失败) | Memory operation failed. |
| [9700002](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700003-系统服务失败) | System service operation failed. |


## isLastWorkTimeOut

```TypeScript
function isLastWorkTimeOut(workId: int, callback: AsyncCallback<boolean>): void
```

检查延迟任务的最后一次执行是否超时，使用Callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-workScheduler-function isLastWorkTimeOut(workId: int, callback: AsyncCallback<boolean>): void--><!--Device-workScheduler-function isLastWorkTimeOut(workId: int, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| workId | int | 是 | 指定延迟任务的Id。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9700004](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700004-workinfo校验失败) | Check on workInfo failed. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: Parameter verification failed. |
| [9700001](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700001-内存操作失败) | Memory operation failed. |
| [9700002](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700003-系统服务失败) | System service operation failed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { workScheduler } from '@kit.BackgroundTasksKit';

workScheduler.isLastWorkTimeOut(500, (error: BusinessError, res: boolean) => {
  if (error) {
    console.error(`workschedulerLog isLastWorkTimeOut failed. code is ${error.code} message is ${error.message}`);
  } else {
    console.info(`workschedulerLog isLastWorkTimeOut success, data is: ${res}`);
  }
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { workScheduler } from '@kit.BackgroundTasksKit';

workScheduler.isLastWorkTimeOut(500, (error: BusinessError<void> | null, res: boolean | undefined) => {
  if (error) {
    console.error(`workschedulerLog isLastWorkTimeOut failed. code is ${error.code} message is ${error.message}`);
  } else {
    console.info(`workschedulerLog isLastWorkTimeOut success, data is: ${res}`);
  }
});
```


## isLastWorkTimeOut

```TypeScript
function isLastWorkTimeOut(workId: int): Promise<boolean>
```

检查延迟任务的最后一次执行是否超时，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-workScheduler-function isLastWorkTimeOut(workId: int): Promise<boolean>--><!--Device-workScheduler-function isLastWorkTimeOut(workId: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| workId | int | 是 | 指定延迟任务的Id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示指定任务的最后一次执行超时，false表示未超时。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9700004](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700004-workinfo校验失败) | Check on workInfo failed. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: Parameter verification failed. |
| [9700001](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700001-内存操作失败) | Memory operation failed. |
| [9700002](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| [9700003](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700003-系统服务失败) | System service operation failed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { workScheduler } from '@kit.BackgroundTasksKit';

workScheduler.isLastWorkTimeOut(500)
  .then((res: boolean) => {
    console.info(`workschedulerLog isLastWorkTimeOut success, data is: ${res}`);
  })
  .catch((error: BusinessError) => {
    console.error(`workschedulerLog isLastWorkTimeOut failed. code is ${error.code} message is ${error.message}`);
  });
```

ArkTS-Sta示例：

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';

workScheduler.isLastWorkTimeOut(500)
  .then((res: boolean) => {
    console.info(`workschedulerLog isLastWorkTimeOut success, data is: ${res}`);
  })
  .catch((error) => {
    console.error(`workschedulerLog isLastWorkTimeOut failed. code is ${error.code} message is ${error.message}`);
  });
```

