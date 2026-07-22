# terminateTask

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## terminateTask

```TypeScript
function terminateTask(longTask: LongTask): void
```

中止任务池中的长时任务，在长时任务执行完成后调用。中止后，执行长时任务的线程可能会被回收。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function terminateTask(longTask: LongTask): void--><!--Device-taskpool-function terminateTask(longTask: LongTask): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| longTask | [LongTask](arkts-arkts-taskpool-longtask-c.md) | 是 | 需要中止的长时任务。 |

**示例：**

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

