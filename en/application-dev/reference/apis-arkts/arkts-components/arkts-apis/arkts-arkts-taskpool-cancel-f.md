# cancel

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## cancel

```TypeScript
function cancel(task: Task): void
```

Cancels a task in the task pool. If the task is in the internal queue of the task pool, the task will not be executed after being canceled, and an exception indicating task cancellation is returned. If the task has been distributed to the worker thread of the task pool, canceling the task does not affect the task execution, and the execution result is returned in the catch branch. You can use **isCanceled()** to check the task cancellation status. In other words, **taskpool.cancel** takes effect for calls of **taskpool.execute**, **taskpool.executeDelayed**, or **taskpool.executePeriodically**. Starting from API version 20, after performing a cancel operation, you can use the generic type BusinessError&lt;[taskpool.TaskResult](arkts-arkts-taskpool-taskresult-i.md)&gt; in the catch branch to obtain the exception information thrown by the task or the final execution result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| task | [Task](arkts-arkts-taskpool-task-c.md) | Yes | Task to cancel. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200015](../errorcode-utils.md#10200015-failed-to-cancel-a-task-that-does-not-exist) | The task to cancel does not exist. |
| [10200016](../errorcode-utils.md#10200016-failed-to-cancel-a-task-being-executed) | The task to cancel is being executed.<br>**Applicable version:** 9 - 17 |
| [10200055](../errorcode-utils.md#10200055-asynchronous-queue-task-canceled) | The asyncRunner task has been canceled.<br>**Applicable version:** 18 and later |

**Examples**

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
    console.info("taskGroup1 res is:" + res);
  });
  taskpool.execute(taskGroup2).then((res: Array<Object>) => {
    console.info("taskGroup2 res is:" + res);
  }).catch((err: BusinessError) => {
    console.error("taskGroup2 catch err: " + err.message);
  });
  setTimeout(() => {
    try {
      taskpool.cancel(taskGroup2);
    } catch (e) {
      console.error(`taskpool: cancel error code: ${e.code}, info: ${e.message}`);
    }
  }, 1000);
}

concurrentFunc();
```

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
    console.error(`taskpool: cancel error code: ${e.code}, info: ${e.message}`);
  }
}

function concurrentFunc() {
  let task = new taskpool.Task(printArgs, 100); // 100: test number
  taskpool.execute(task).catch((err: BusinessError) => {
    console.error("taskpool catch err: " + err.message);
  });
  setTimeout(() => {
    let cancelTask = new taskpool.Task(cancelFunction, task.taskId);
    taskpool.execute(cancelTask);
  }, 1000);
}

concurrentFunc();
```


<a id="cancel-1"></a>

## cancel

```TypeScript
function cancel(group: TaskGroup): void
```

Cancels a task group in the task pool. If a task group is canceled before all the tasks in it are finished, **undefined** is returned. Starting from API version 20, after performing a cancel operation, you can use the generic type BusinessError&lt;[taskpool.TaskResult](arkts-arkts-taskpool-taskresult-i.md)&gt; in the catch branch to obtain the exception information thrown by the task or the final execution result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| group | [TaskGroup](arkts-arkts-taskpool-taskgroup-c.md) | Yes | Task group to cancel. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200018](../errorcode-utils.md#10200018-failed-to-cancel-a-task-group-that-does-not-exist) | The task group to cancel does not exist. |

**Examples**

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
    console.info("taskGroup1 res is:" + res);
  });
  taskpool.execute(taskGroup2).then((res: Array<Object>) => {
    console.info("taskGroup2 res is:" + res);
  }).catch((err: BusinessError) => {
    console.error("taskGroup2 catch err: " + err.message);
  });
  setTimeout(() => {
    try {
      taskpool.cancel(taskGroup2);
    } catch (e) {
      console.error(`taskpool: cancel error code: ${e.code}, info: ${e.message}`);
    }
  }, 1000);
}

concurrentFunc();
```


<a id="cancel-2"></a>

## cancel

```TypeScript
function cancel(taskId: number): void
```

Cancels a task in the task pool by task ID. If the task is in the internal queue of the task pool, the task will not be executed after being canceled, and an exception indicating task cancellation is returned. If the task has been distributed to the worker thread of the task pool, canceling the task does not affect the task execution, and the execution result is returned in the catch branch. You can use **isCanceled()** to check the task cancellation status. **taskpool.cancel** takes effect for the previous calls of **taskpool.execute** or **taskpool.executeDelayed**. If **taskpool.cancel** is called by other threads, note that the cancel operation, which is asynchronous, may take effect for later calls of **taskpool.execute** or **taskpool.executeDelayed**. Starting from API version 20, after performing a cancel operation, you can use the generic type BusinessError&lt;[taskpool.TaskResult](arkts-arkts-taskpool-taskresult-i.md)&gt; in the catch branch to obtain the exception information thrown by the task or the final execution result.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | number | Yes | ID of the task to cancel. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200015](../errorcode-utils.md#10200015-failed-to-cancel-a-task-that-does-not-exist) | The task to cancel does not exist. |
| [10200055](../errorcode-utils.md#10200055-asynchronous-queue-task-canceled) | The asyncRunner task has been canceled. |

**Examples**

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
    console.error(`taskpool: cancel error code: ${e.code}, info: ${e.message}`);
  }
}

function concurrentFunc() {
  let task = new taskpool.Task(printArgs, 100); // 100: test number
  taskpool.execute(task).catch((err: BusinessError) => {
    console.error("taskpool catch err: " + err.message);
  });
  setTimeout(() => {
    let cancelTask = new taskpool.Task(cancelFunction, task.taskId);
    taskpool.execute(cancelTask);
  }, 1000);
}

concurrentFunc();
```
