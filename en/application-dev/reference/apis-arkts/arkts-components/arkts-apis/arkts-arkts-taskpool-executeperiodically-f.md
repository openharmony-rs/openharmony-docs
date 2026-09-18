# executePeriodically

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## executePeriodically

```TypeScript
function executePeriodically(period: number, task: Task, priority?: Priority): void
```

Executes a task periodically. In this execution mode, you can set the task priority and call **cancel()** to cancel the execution. A periodic task cannot be a task in a task group, serial queue, or asynchronous queue. It cannot call **execute()** again or have a dependency relationship.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| period | number | Yes | Execution period, in ms. The value must be greater than or equal to 0. The value should be an integer.<br>Unit:milliseconds. |
| task | [Task](arkts-arkts-taskpool-task-c.md) | Yes | Task to be executed. |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | No | Priority of the task. The default value is **taskpool.Priority.MEDIUM**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker-data-serialization-exception) | An exception occurred during serialization. |
| [10200014](../errorcode-utils.md#10200014-non-concurrent-function-error) | The function is not marked as concurrent. |
| [10200028](../errorcode-utils.md#10200028-delay-less-than-zero) | The period is less than zero. |
| [10200050](../errorcode-utils.md#10200050-concurrent-task-that-has-been-executed-cannot-be-executed-periodically) | The concurrent task has been executed and cannot be executed periodically. |
| [10200057](../errorcode-utils.md#10200057-task-cannot-be-executed-by-two-apis) | The task cannot be executed by two APIs.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
@Concurrent
function printArgs(args: number): void {
  console.info("printArgs: " + args);
}

@Concurrent
function testExecutePeriodically(args: number): void {
  let t = Date.now();
  while ((Date.now() - t) < args) {
    continue;
  }
  taskpool.Task.sendData(args); // Send a message to the host thread.
}

function printResult(data: number): void {
  console.info("taskpool: data is: " + data);
}

function taskpoolTest() {
  try {
    let task: taskpool.Task = new taskpool.Task(printArgs, 100); // 100: test number
    taskpool.executePeriodically(1000, task); // 1000: period is 1000ms
  } catch (e) {
    console.error(`taskpool execute-1: Code: ${e.code}, message: ${e.message}`);
  }

  try {
    let periodicTask: taskpool.Task = new taskpool.Task(testExecutePeriodically, 200); // 200: test number
    periodicTask.onReceiveData(printResult);
    taskpool.executePeriodically(1000, periodicTask); // 1000: period is 1000ms
  } catch (e) {
    console.error(`taskpool execute-2: Code: ${e.code}, message: ${e.message}`);
  }
}

taskpoolTest();
```

```TypeScript
@Concurrent
function printArgs(args: number): void {
  console.info("printArgs: " + args);
}

@Concurrent
function testExecutePeriodically(args: number): void {
  let t = Date.now();
  while ((Date.now() - t) < args) {
    continue;
  }
  taskpool.Task.sendData(args); // Send a message to the host thread.
}

function printResult(data: number): void {
  console.info("taskpool: data is: " + data);
}

function taskpoolTest() {
  try {
    let task: taskpool.Task = new taskpool.GenericsTask<[number], void>(printArgs, 100); // 100: test number
    taskpool.executePeriodically<[number], void>(1000, task); // 1000: period is 1000ms
  } catch (e) {
    console.error(`taskpool execute-1: Code: ${e.code}, message: ${e.message}`);
  }

  try {
    let periodicTask: taskpool.Task = new taskpool.GenericsTask<[number], void>(testExecutePeriodically, 200); // 200: test number
    periodicTask.onReceiveData(printResult);
    taskpool.executePeriodically<[number], void>(1000, periodicTask); // 1000: period is 1000ms
  } catch (e) {
    console.error(`taskpool execute-2: Code: ${e.code}, message: ${e.message}`);
  }
}

taskpoolTest();
```


## executePeriodically

```TypeScript
function executePeriodically<A extends Array<Object>, R>(period: number, task: GenericsTask<A, R>, priority?: Priority): void
```

Executes a generic task periodically, without verifying the parameter type and return value type of the task. The verification of the **executePeriodically** task works in conjunction with **new GenericsTask**, requiring that the parameter and return value types match those specified in **new GenericsTask**.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| period | number | Yes | Execution period, in ms. The value must be greater than or equal to 0. The value should be an integer.<br>Unit:milliseconds. |
| task | [GenericsTask](arkts-arkts-taskpool-genericstask-c.md)&lt;A, R&gt; | Yes | Generic task to be executed periodically. |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | No | Priority of the task. The default value is **taskpool.Priority.MEDIUM**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker-data-serialization-exception) | An exception occurred during serialization. |
| [10200014](../errorcode-utils.md#10200014-non-concurrent-function-error) | The function is not marked as concurrent. |
| [10200028](../errorcode-utils.md#10200028-delay-less-than-zero) | The period is less than zero. |
| [10200050](../errorcode-utils.md#10200050-concurrent-task-that-has-been-executed-cannot-be-executed-periodically) | The concurrent task has been executed and cannot be executed periodically. |
| [10200057](../errorcode-utils.md#10200057-task-cannot-be-executed-by-two-apis) | The task cannot be executed by two APIs.<br>**Applicable version:** 18 and later |

**Examples**

See [executePeriodically](#executeperiodically)
