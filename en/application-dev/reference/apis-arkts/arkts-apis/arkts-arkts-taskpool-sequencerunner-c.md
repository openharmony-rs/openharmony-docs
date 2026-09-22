# SequenceRunner

```TypeScript
class SequenceRunner
```

Implements a serial queue, in which all tasks are executed in sequence.

**Since:** 11

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(priority?: Priority)
```

A constructor used to create a **SequenceRunner** instance.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | No | Priority of the task. The default value is **taskpool.Priority.MEDIUM**. |

**Examples**

```TypeScript
let runner: taskpool.SequenceRunner = new taskpool.SequenceRunner();
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(name: string, priority?: Priority)
```

A constructor used to create a **SequenceRunner** instance. This instance represents a global serial queue. If the passed-in name is the same as an existing name, the same serial queue is returned.

> **NOTE:** 
> 
> - The bottom layer uses the singleton mode to ensure that the same instance is obtained when a serial queue with the same name is created.
> 
> - The priority of a serial queue cannot be modified.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of a serial queue. |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | No | Priority of the task. The default value is **taskpool.Priority.MEDIUM**. |

**Examples**

```TypeScript
let runner:taskpool.SequenceRunner = new taskpool.SequenceRunner("runner1", taskpool.Priority.LOW);
```

## execute

```TypeScript
execute(task: Task): Promise<Object>
```

Adds a task to the serial queue for execution. Before using this API, you must create a **SequenceRunner** instance. Tasks in another task group, serial queue, or asynchronous queue, dependent tasks, and tasks that have been executed cannot be added to the serial queue. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Tasks that depend others cannot be added to the serial queue.
> 
> - The failure or cancellation of a task does not affect the execution of subsequent tasks in the serial queue.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| task | [Task](arkts-arkts-taskpool-task-c.md) | Yes | Task to be added to the serial queue. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Object&gt; | Promise used to return the task execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200003](../errorcode-utils.md#10200003-failed-to-initialize-the-worker-instance) | Worker initialization failed.<br>**Applicable version:** 11 - 17 |
| [10200006](../errorcode-utils.md#10200006-worker-data-serialization-exception) | An exception occurred during serialization. |
| [10200025](../errorcode-utils.md#10200025-failed-to-add-a-task-with-dependent-tasks-to-the-queue) | dependent task not allowed. |
| [10200051](../errorcode-utils.md#10200051-periodic-task-cannot-be-executed-again) | The periodic task cannot be executed again.<br>**Applicable version:** 12 and later |
| [10200057](../errorcode-utils.md#10200057-task-cannot-be-executed-by-two-apis) | The task cannot be executed by two APIs.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
@Concurrent
function additionDelay(delay: number): void {
  let start: number = new Date().getTime();
  while (new Date().getTime() - start < delay) {
    continue;
  }
}
@Concurrent
function waitForRunner(finalString: string): string {
  return finalString;
}
async function seqRunner() {
  let finalString:string = "";
  let task1:taskpool.Task = new taskpool.Task(additionDelay, 3000);
  let task2:taskpool.Task = new taskpool.Task(additionDelay, 2000);
  let task3:taskpool.Task = new taskpool.Task(additionDelay, 1000);
  let task4:taskpool.Task = new taskpool.Task(waitForRunner, finalString);

  let runner:taskpool.SequenceRunner = new taskpool.SequenceRunner();
  runner.execute(task1).then(() => {
    finalString += 'a';
    console.info("seqrunner: task1 done.");
  });
  runner.execute(task2).then(() => {
    finalString += 'b';
    console.info("seqrunner: task2 done");
  });
  runner.execute(task3).then(() => {
    finalString += 'c';
    console.info("seqrunner: task3 done");
  });
  await runner.execute(task4);
  console.info("seqrunner: task4 done, finalString is " + finalString);
}
```
