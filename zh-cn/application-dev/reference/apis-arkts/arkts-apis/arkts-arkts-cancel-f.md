# cancel

## cancel

```TypeScript
function cancel(task: Task): void
```

取消任务池中的任务。当任务在taskpool等待队列中，取消该任务后该任务将不再执行，并返回任务被取消的异常；当任务已经在taskpool工作线程执行，
取消该任务并不影响任务继续执行，执行结果在catch分支返回，搭配**isCanceled()**可以对任务取消行为作出响应。也就是说，
**taskpool.cancel**对其之前的**taskpool.execute**、**taskpool.executeDelayed**或**taskpool.executePeriodically**生效。
从API version 20开始，在执行cancel操作后，可以在catch分支里使用泛型BusinessError<
[taskpool.TaskResult](arkts-arkts-taskresult-i.md)>，来获取任务中抛出的异常信息或最终的执行结果。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | Task | 是 | 需要取消执行的任务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200015](../errorcode-utils.md#10200015-取消不存在的任务错误) | The task to cancel does not exist. |
| [10200016](../errorcode-utils.md#10200016-取消正在执行的任务错误) | The task to cancel is being executed.<br>**适用版本：** 9 - 17 |
| [10200055](../errorcode-utils.md#10200055-异步任务被取消) | The asyncRunner task has been canceled.<br>**适用版本：** 18+ |


## cancel

```TypeScript
function cancel(group: TaskGroup): void
```

取消任务池中的任务组。如果任务组中的任务未全部执行结束，返回**undefined**。
从API version 20开始，在执行cancel操作后，可以在catch分支里使用泛型BusinessError<
[taskpool.TaskResult](arkts-arkts-taskresult-i.md)>，来获取任务中抛出的异常信息或最终的执行结果。

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| group | TaskGroup | 是 | 需要取消执行的任务组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200018](../errorcode-utils.md#10200018-取消不存在的任务组错误) | The task group to cancel does not exist. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

@Concurrent
function printArgs(args: number): number {
  let t: number = Date.now();
  while (Date.now() - t < 2000) {
    continue;
  }
  console.info("printArgs: " + args);
  return args;
}

function concurrentFunc() {
  let taskGroup1: taskpool.TaskGroup = new taskpool.TaskGroup();
  taskGroup1.addTask(printArgs, 10); // 10: test number
  let taskGroup2: taskpool.TaskGroup = new taskpool.TaskGroup();
  taskGroup2.addTask(printArgs, 100); // 100: test number
  taskpool.execute(taskGroup1).then((res: Array<Object>) => {
    console.info(`Succeeded in executing task. res is: ` + res);
  });
  taskpool.execute(taskGroup2).then((res: Array<Object>) => {
    console.info(`Succeeded in executing task. res is: ` + res);
  }).catch((err: BusinessError) => {
    console.error(`Failed to execute task. Code: ${err.code}, message: ${err.message}`);
  });
  setTimeout(() => {
    try {
      taskpool.cancel(taskGroup2);
    } catch (e) {
      console.error(`Failed to cancel task. Code: ${e.code}, message: ${e.message}`);
    }
  }, 1000);
}

concurrentFunc();

```


## cancel

```TypeScript
function cancel(taskId: number): void
```

通过任务ID取消任务池中的任务。如果任务在taskpool等待队列中，取消后任务将不再执行，并返回任务取消的异常。如果任务已在taskpool工作线程中执行，
取消不影响任务继续执行，执行结果在catch分支返回，搭配**isCanceled()**可以对任务取消行为作出响应。**taskpool.cancel**对其之前的
**taskpool.execute**或**taskpool.executeDelayed**生效。在其他线程调用**taskpool.cancel**时，需注意其行为是异步的，
可能影响之后的**taskpool.execute**或**taskpool.executeDelayed**。
从API version 20开始，在执行cancel操作后，可以在catch分支里使用泛型BusinessError<
[taskpool.TaskResult](arkts-arkts-taskresult-i.md)>，来获取任务中抛出的异常信息或最终的执行结果。

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | number | 是 | 需要取消执行的任务的ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200015](../errorcode-utils.md#10200015-取消不存在的任务错误) | The task to cancel does not exist. |
| [10200055](../errorcode-utils.md#10200055-异步任务被取消) | The asyncRunner task has been canceled. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

@Concurrent
function printArgs(args: number): number {
  let t: number = Date.now();
  while (Date.now() - t < 2000) {
    continue;
  }
  if (taskpool.Task.isCanceled()) {
    console.info("task has been canceled after 2s sleep.");
    return args + 1;
  }
  console.info("printArgs: " + args);
  return args;
}

@Concurrent
function cancelFunction(taskId: number) {
  try {
    taskpool.cancel(taskId);
  } catch (e) {
    console.error(`Failed to cancel task. Code: ${e.code}, message: ${e.message}`);
  }
}

function concurrentFunc() {
  let task = new taskpool.Task(printArgs, 100); // 100: test number
  taskpool.execute(task).catch((err: BusinessError) => {
    console.error(`Failed to execute task. Code: ${err.code}, message: ${err.message}`);
  });
  setTimeout(() => {
    let cancelTask = new taskpool.Task(cancelFunction, task.taskId);
    taskpool.execute(cancelTask);
  }, 1000);
}

concurrentFunc();

```

