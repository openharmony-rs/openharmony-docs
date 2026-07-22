# AsyncRunner

表示异步队列，可以指定任务执行的并发度和排队策略。

**起始版本：** 18

<!--Device-taskpool-export class AsyncRunner--><!--Device-taskpool-export class AsyncRunner-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(runningCapacity: number, waitingCapacity?: number)
```

AsyncRunner的构造函数，用于创建一个**AsyncRunner**实例。构造一个非全局的异步队列，即使传入的参数相同，也会返回不同的异步队列。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncRunner-constructor(runningCapacity: number, waitingCapacity?: number)--><!--Device-AsyncRunner-constructor(runningCapacity: number, waitingCapacity?: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| runningCapacity | number | 是 | 指定任务执行的最大并发度，该值必须为正整数。如果传入负数，会报错；如果传入非整数，会向下取整。 |
| waitingCapacity | number | 否 | 指定等待任务的列表容量，该值必须大于等于0。如果传入负数，会报错；如果传入非整数，会向下取整。默认值为**0**，表示等待任务列表的容量没有限制。如果传入大于0的值，则表示排队策略为丢弃策略，当加入的任务数量超过该值时，等待列表中处于队头的任务会被丢弃。 |

**示例：**

```TypeScript
let runner: taskpool.AsyncRunner = new taskpool.AsyncRunner(5);

```

## constructor

```TypeScript
constructor(name: string, runningCapacity: number, waitingCapacity?: number)
```

AsyncRunner的构造函数，用于创建一个**AsyncRunner**实例。构造一个全局异步队列，如果队列名称与已有名称相同，将返回同一个异步队列。
> **说明**  
>  
> - 底层通过单例模式确保创建同名的异步队列时，获取同一个实例。  
>  
> - 无法修改并发度和等待任务列表容量。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncRunner-constructor(name: string, runningCapacity: number, waitingCapacity?: number)--><!--Device-AsyncRunner-constructor(name: string, runningCapacity: number, waitingCapacity?: number)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 异步队列的名字。 |
| runningCapacity | number | 是 | 指定任务执行的最大并发度，该值必须为正整数。如果传入负数，会报错；如果传入非整数，会向下取整。 |
| waitingCapacity | number | 否 | 指定等待任务的列表容量，该值必须大于等于0。如果传入负数，会报错；如果传入非整数，会向下取整。默认值为**0**，表示等待任务列表的容量没有限制。如果传入大于0的值，则表示排队策略为丢弃策略，当加入的任务数量超过该值时，等待列表中处于队头的任务会被丢弃。 |

**示例：**

```TypeScript
let runner:taskpool.AsyncRunner = new taskpool.AsyncRunner("runner1", 5, 5);

```

## execute

```TypeScript
execute(task: Task, priority?: Priority): Promise<Object>
```

执行异步任务。使用该方法前需要先构造**AsyncRunner**实例。使用Promise异步回调。
> **说明**  
>  
> - 不支持执行任务组中的任务。  
>  
> - 不支持执行串行队列中的任务。  
>  
> - 不支持执行其他异步队列任务。  
>  
> - 不支持执行周期性任务。  
>  
> - 不支持执行延迟任务。  
>  
> - 不支持执行存在依赖的任务。  
>  
> - 不支持执行已执行过的任务。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AsyncRunner-execute(task: Task, priority?: Priority): Promise<Object>--><!--Device-AsyncRunner-execute(task: Task, priority?: Priority): Promise<Object>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | [Task](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-task-i.md) | 是 | 需要添加到异步队列中的任务。 |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | 否 | 指定任务的优先级，默认值为**taskpool.Priority.MEDIUM**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Object&gt; | Promise对象，返回任务执行的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200025](../errorcode-utils.md#10200025-串行队列中添加了存在依赖的任务) | dependent task not allowed. |
| [10200051](../errorcode-utils.md#10200051-无法再次执行周期任务) | The periodic task cannot be executed again. |
| [10200054](../errorcode-utils.md#10200054-异步队列任务被丢弃) | The asyncRunner task is discarded. |
| [10200057](../errorcode-utils.md#10200057-任务无法被两种api执行) | The task cannot be executed by two APIs. |

**示例：**

```TypeScript
import { taskpool } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

@Concurrent
function additionDelay(delay: number): void {
  let start: number = new Date().getTime();
  while (new Date().getTime() - start < delay) {
    continue;
  }
}
async function asyncRunner() {
  let runner:taskpool.AsyncRunner = new taskpool.AsyncRunner("runner1", 5, 5);
  for (let i = 0; i < 30; i++) {
    let task:taskpool.Task = new taskpool.Task(additionDelay, 1000);
    runner.execute(task).then(() => {
      console.info("asyncRunner: task" + i + " done.");
    }).catch((e: BusinessError) => {
      console.error("asyncRunner: task" + i + " error." + e.code + "-" + e.message);
    });
  }
}

async function asyncRunner2() {
  let runner:taskpool.AsyncRunner = new taskpool.AsyncRunner(5);
  for (let i = 0; i < 20; i++) {
    let task:taskpool.Task = new taskpool.Task(additionDelay, 1000);
    runner.execute(task).then(() => {
      console.info("asyncRunner: task" + i + " done.");
    });
  }
}

```

