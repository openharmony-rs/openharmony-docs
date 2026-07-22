# getTask

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## getTask

```TypeScript
function getTask(taskId: number, taskName?: string): Task | undefined
```

通过taskId或taskId与taskName获取对应的Task实例。
> **说明**  
>  
> - 如果传入的taskId查询不到对应的Task实例，则会返回**undefined**。  
>  
> - 如果传入的taskId能够查询到对应的Task实例，但是调用**getTask**方法的线程和创建Task实例的线程不一致，则会返回**undefined**。  
>  
> - 如果同时传入taskId和taskName，通过taskId查询到的Task实例的name和传入的taskName不一致，则会返回**undefined**。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function getTask(taskId: number, taskName?: string): Task | undefined--><!--Device-taskpool-function getTask(taskId: number, taskName?: string): Task | undefined-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | number | 是 | 任务ID。该值应为整数。 |
| taskName | string | 否 | 任务名称。默认值为**undefined**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Task](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-task-i.md) | Task实例；当情况异常时，返回**undefined**，具体可见上文说明。 |

**示例：**

```TypeScript
import { taskpool } from '@kit.ArkTS';

@Concurrent
function addNum(num1: number, num2: number) {
  return num1 + num2;
}

function checkTask() {
  try {
    taskpool.getTask(null);
  } catch (e) {
    console.error("error:" + e);
    // error:BusinessError: Parameter error. The input parameters are invalid, the type of the first param must be number.
  }

  let task1:taskpool.Task = new taskpool.Task("addNum", addNum, 1, 2);
  let task2:taskpool.Task | undefined = taskpool.getTask(task1.taskId, "addNum"); // task2 is not undefined
  let task3:taskpool.Task | undefined = taskpool.getTask(task1.taskId, "add"); // task3 is undefined
  let task4:taskpool.Task | undefined = taskpool.getTask(0); // task4 is undefined
}

function dealTask() {
  let task1:taskpool.Task = new taskpool.Task(addNum, 1, 2);
  let task2:taskpool.Task | undefined = taskpool.getTask(task1.taskId);
  if (task2 === undefined) {
    return;
  }

  taskpool.execute(task2).then((result) => {
    console.info("task2 result: " + result); // task2 result: 3
  })
}

```

