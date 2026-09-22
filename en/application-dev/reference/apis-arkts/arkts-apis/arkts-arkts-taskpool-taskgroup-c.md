# TaskGroup

```TypeScript
class TaskGroup
```

Implements a task group, in which tasks are associated with each other and all tasks are executed at a time. If all the tasks are executed normally, an array of task results is returned asynchronously, and the sequence of elements in the array is the same as the sequence of tasks added by calling [addTask](#addtask-1). If any task fails, the corresponding exception is thrown. If multiple tasks in the task group fail, the exception of the first failed task is thrown. A task group can be executed for multiple times, but no task can be added after the task group is executed.

**Since:** 10

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## addTask

```TypeScript
addTask(func: Function, ...args: Object[]): void
```

Adds the function to be executed to this task group. Before using this API, you must create a **TaskGroup** instance.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| func | Function | Yes | Function that must be decorated using [@Concurrent](../../../arkts-utils/taskpool-introduction.md#concurrent-decorator). For details about the supported return value types, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). |
| args | Object[] | Yes | Arguments of the function. For details about the supported parameter types, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). The default value is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200014](../errorcode-utils.md#10200014-non-concurrent-function-error) | The function is not marked as concurrent. |

**Examples**

```TypeScript
@Concurrent
function printArgs(args: number): number {
  console.info("printArgs: " + args);
  return args;
}

let taskGroup: taskpool.TaskGroup = new taskpool.TaskGroup();
taskGroup.addTask(printArgs, 100); // 100: test number
```

<a id="addtask-1"></a>

## addTask

```TypeScript
addTask(task: Task): void
```

Adds a created task to this task group. Before using this API, you must create a **TaskGroup** instance. Tasks in another task group, serial queue, or asynchronous queue, dependent tasks, continuous tasks, tasks that have been executed, and periodic tasks cannot be added to the task group.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| task | [Task](arkts-arkts-taskpool-task-c.md) | Yes | Task to be added to the task group. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200014](../errorcode-utils.md#10200014-non-concurrent-function-error) | The function is not marked as concurrent. |
| [10200051](../errorcode-utils.md#10200051-periodic-task-cannot-be-executed-again) | The periodic task cannot be executed again.<br>**Applicable version:** 12 and later |
| [10200057](../errorcode-utils.md#10200057-task-cannot-be-executed-by-two-apis) | The task cannot be executed by two APIs.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
@Concurrent
function printArgs(args: number): number {
  console.info("printArgs: " + args);
  return args;
}

let taskGroup: taskpool.TaskGroup = new taskpool.TaskGroup();
let task: taskpool.Task = new taskpool.Task(printArgs, 200); // 200: test number
taskGroup.addTask(task);
```

## constructor

```TypeScript
constructor()
```

Constructor used to create a **TaskGroup** instance.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let taskGroup = new taskpool.TaskGroup();
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(name: string)
```

A constructor used to create a **TaskGroup** instance, with the task group name specified.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Task group name. |

**Examples**

```TypeScript
let taskGroupName: string = "groupName";
let taskGroup: taskpool.TaskGroup = new taskpool.TaskGroup(taskGroupName);
let name: string = taskGroup.name;
```

## name

```TypeScript
name: string
```

Name of the task group specified when the task group is created.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
