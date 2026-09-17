# executeDelayed

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## executeDelayed

```TypeScript
function executeDelayed(delayTime: number, task: Task, priority?: Priority): Promise<Object>
```

Executes a task after a given delay. In this execution mode, you can set the task priority and call **cancel()** to cancel the execution. The task cannot be a task in a task group, serial queue, or asynchronous queue, or a periodic task. This API can be called only once for a continuous task, but multiple times for a non-continuous task. This API uses a promise to return the result.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| delayTime | number | Yes | Delay, in ms. The value must be greater than or equal to 0. The value should be an integer.<br>Unit:milliseconds. |
| task | [Task](arkts-arkts-taskpool-task-c.md) | Yes | Task to be executed with a delay. |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | No | Priority of the task. The default value is **taskpool.Priority.MEDIUM**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Object&gt; | Promise used to return an object that carries the function execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200028](../errorcode-utils.md#10200028-delay-less-than-zero) | The delayTime is less than zero. |
| [10200006](../errorcode-utils.md#10200006-worker-data-serialization-exception) | An exception occurred during serialization.<br>**Applicable version:** 12 and later |
| [10200014](../errorcode-utils.md#10200014-non-concurrent-function-error) | The function is not marked as concurrent.<br>**Applicable version:** 12 and later |
| [10200051](../errorcode-utils.md#10200051-periodic-task-cannot-be-executed-again) | The periodic task cannot be executed again.<br>**Applicable version:** 12 and later |
| [10200057](../errorcode-utils.md#10200057-task-cannot-be-executed-by-two-apis) | The task cannot be executed by two APIs.<br>**Applicable version:** 18 and later |

**Examples**

```TypeScript
// import BusinessError
import { BusinessError } from '@kit.BasicServicesKit';

@Concurrent
function printArgs(args: number): void {
    console.info("printArgs: " + args);
}

let t: number = Date.now();
console.info("taskpool start time is: " + t);
let task: taskpool.Task = new taskpool.Task(printArgs, 100); // 100: test number
taskpool.executeDelayed(1000, task).then(() => { // 1000: delayTime is 1000ms
  console.info("taskpool execute success");
}).catch((e: BusinessError) => {
  console.error(`taskpool execute: Code: ${e.code}, message: ${e.message}`);
})
```

```TypeScript
// import BusinessError
import { BusinessError } from '@kit.BasicServicesKit'

@Concurrent
function printArgs(args: number): string {
    console.info("printArgs: " + args);
    return "success";
}

let task: taskpool.Task = new taskpool.GenericsTask<[number], string>(printArgs, 100); // 100: test number
taskpool.executeDelayed<[number], string>(1000, task).then((res: string) => { // 1000: delayTime is 1000ms
  console.info("taskpool execute success");
}).catch((e: BusinessError) => {
  console.error(`taskpool execute: Code: ${e.code}, message: ${e.message}`);
})
```


## executeDelayed

```TypeScript
function executeDelayed<A extends Array<Object>, R>(delayTime: number, task: GenericsTask<A, R>, priority?: Priority): Promise<R>
```

Executes the generic task with a delay without verifying the parameter type and return value type of the task. This API uses a promise to return the result. The verification of the **executeDelayed** task works in conjunction with **new GenericsTask**, requiring that the parameter and return value types match those specified in **new GenericsTask**.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| delayTime | number | Yes | Delay, in ms. The value must be greater than or equal to 0. The value should be an integer.<br>Unit:milliseconds. |
| task | [GenericsTask](arkts-arkts-taskpool-genericstask-c.md)&lt;A, R&gt; | Yes | Generic task to be executed with a delay. |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | No | Priority of the task. The default value is **taskpool.Priority.MEDIUM**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;R&gt; | Promise used to return an object that carries the function execution result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200028](../errorcode-utils.md#10200028-delay-less-than-zero) | The delayTime is less than zero. |
| [10200051](../errorcode-utils.md#10200051-periodic-task-cannot-be-executed-again) | The periodic task cannot be executed again. |
| [10200057](../errorcode-utils.md#10200057-task-cannot-be-executed-by-two-apis) | The task cannot be executed by two APIs.<br>**Applicable version:** 18 and later |

**Examples**

See [executeDelayed](#executedelayed)
