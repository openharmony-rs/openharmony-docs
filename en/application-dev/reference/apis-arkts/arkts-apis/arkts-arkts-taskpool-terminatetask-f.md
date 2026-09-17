# terminateTask

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## terminateTask

```TypeScript
function terminateTask(longTask: LongTask): void
```

Terminates a continuous task in the task pool. It is called after the continuous task is complete. After the task is terminated, the thread that executes the task may be reclaimed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| longTask | [LongTask](arkts-arkts-taskpool-longtask-c.md) | Yes | Continuous task to terminate. |

**Examples**

```TypeScript
@Concurrent
function longTask(arg: number): number {
  let t: number = Date.now();
  while (Date.now() - t < arg) {
    continue;
  }
  console.info("longTask has been executed.");
  return arg;
}

function concurrentFunc() {
  let task1: taskpool.LongTask = new taskpool.LongTask(longTask, 1000); // 1000: sleep time
  taskpool.execute(task1).then((res: Object) => {
    taskpool.terminateTask(task1);
    console.info("taskpool longTask result: " + res);
  });
}

concurrentFunc();
```
