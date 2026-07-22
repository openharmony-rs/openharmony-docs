# obtainAllWorks

## 导入模块

```TypeScript
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## obtainAllWorks

```TypeScript
function obtainAllWorks(callback: AsyncCallback<void>): Array<WorkInfo>
```

获取当前应用所有的延迟任务，使用Callback异步回调。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [obtainAllWorks(callback:](arkts-backgroundtasks-workscheduler-obtainallworks-f.md#obtainallworks)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-workScheduler-function obtainAllWorks(callback: AsyncCallback<void>): Array<WorkInfo>--><!--Device-workScheduler-function obtainAllWorks(callback: AsyncCallback<void>): Array<WorkInfo>-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，获取成功时，err为undefined，否则为错误对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;WorkInfo&gt; | 延迟任务列表，如果已添加延迟任务到执行队列，则返回当前应用所有的延迟任务列表；否则返回空列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameters types. |
| [9700001](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700001-内存操作失败) | Memory operation failed. |
| [9700002](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700002-parcel读写操作失败) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;2. Failed to apply for memory. |
| [9700003](../../apis-backgroundtasks-kit/errorcode-workScheduler.md#9700003-系统服务失败) | System service operation failed. |


## obtainAllWorks

```TypeScript
function obtainAllWorks(callback: AsyncCallback<Array<WorkInfo>>): void
```

获取当前应用所有的延迟任务，使用Callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-workScheduler-function obtainAllWorks(callback: AsyncCallback<Array<WorkInfo>>): void--><!--Device-workScheduler-function obtainAllWorks(callback: AsyncCallback<Array<WorkInfo>>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;WorkInfo&gt;&gt; | 是 | 回调函数，获取成功时，返回当前应用所有的延迟任务列表，否则抛出异常。 |

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

workScheduler.obtainAllWorks((error: BusinessError, res: Array<workScheduler.WorkInfo>) => {
  if (error) {
    console.error(`workschedulerLog obtainAllWorks failed. code is ${error.code} message is ${error.message}`);
  } else {
    console.info(`workschedulerLog obtainAllWorks success, data is: ${JSON.stringify(res)}`);
  }
});

```


## obtainAllWorks

```TypeScript
function obtainAllWorks(): Promise<Array<WorkInfo>>
```

获取当前应用所有的延迟任务，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-workScheduler-function obtainAllWorks(): Promise<Array<WorkInfo>>--><!--Device-workScheduler-function obtainAllWorks(): Promise<Array<WorkInfo>>-End-->

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;WorkInfo&gt;&gt; | Promise对象，返回当前应用所有的延迟任务。 |

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

workScheduler.obtainAllWorks().then((res: Array<workScheduler.WorkInfo>) => {
  console.info(`workschedulerLog obtainAllWorks success, data is: ${JSON.stringify(res)}`);
}).catch((error: BusinessError) => {
  console.error(`workschedulerLog obtainAllWorks failed. code is ${error.code} message is ${error.message}`);
})

```

