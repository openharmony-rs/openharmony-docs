# getTask

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## getTask

```TypeScript
function getTask(taskId: number, taskName?: string): Task | undefined
```

Obtains the corresponding task instance by task ID, or by task ID and task name.

> **NOTE:** 
> 
> - If no task instance is found based on the input task ID, **undefined** is returned.
> 
> - If the corresponding task instance can be queried based on the input task ID but the thread that calls the
> **getTask** method is different from the thread that creates the task instance, **undefined** is returned.
> 
> - If taskId and taskName are both passed, and the name of the task instance queried via task ID does not match the provided task name, **undefined** is returned.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| taskId | number | Yes | Task ID. The value should be an integer. |
| taskName | string | No | Task name. The default value is **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Task](arkts-arkts-taskpool-task-c.md) &#124; undefined | Task instance. If an exception occurs, **undefined** is returned. For details, see the preceding description. |

**Examples**

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
