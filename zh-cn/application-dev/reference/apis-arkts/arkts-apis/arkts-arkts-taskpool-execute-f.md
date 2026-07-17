# execute

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## execute

```TypeScript
function execute(func: Function, ...args: Object[]): Promise<Object>
```

将待执行的函数放入taskpool的内部任务队列，函数不会立即执行，而是等待分发到工作线程执行。在当前执行模式下，不支持取消任务。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function execute(func: Function, ...args: Object[]): Promise<Object>--><!--Device-taskpool-function execute(func: Function, ...args: Object[]): Promise<Object>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| func | Function | 是 | 执行的逻辑需要传入函数，该函数必须使用[@Concurrent装饰器](../../../../arkts-utils/taskpool-introduction.md#concurrent装饰器)装饰。支持的函数返回值类型请参考[序列化支持类型](../../../../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。 |
| args | Object[] | 是 | 任务执行传入函数的入参，支持的参数类型请参考[序列化支持类型](../../../../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。默认值为**undefined**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<unknown> | <br>**适用版本：** 9 - 11 |
| Promise<Object> | Promise对象，返回任务函数的执行结果。<br>**适用版本：** 11+ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200003](../errorcode-utils.md#10200003-worker初始化失败) | Worker initialization failed.<br>**适用版本：** 9 - 11 |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: number): number {
    console.info("printArgs: " + args);
    return args;
}

taskpool.execute(printArgs, 100).then((value: Object) => { // 100: test number
  console.info("taskpool result: " + value);
});

```


## execute

```TypeScript
function execute<A extends Array<Object>, R>(func: (...args: A) => R | Promise<R>, ...args: A): Promise<R>
```

校验并发函数的参数类型和返回值类型后，将函数添加到taskpool的任务队列。使用Promise异步回调。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function execute<A extends Array<Object>, R>(func: (...args: A) => R | Promise<R>, ...args: A): Promise<R>--><!--Device-taskpool-function execute<A extends Array<Object>, R>(func: (...args: A) => R | Promise<R>, ...args: A): Promise<R>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| func | (...args: A) => R \| Promise<R> | 是 | 执行的逻辑需要传入函数，该函数必须使用[@Concurrent装饰器](../../../../arkts-utils/taskpool-introduction.md#concurrent装饰器)装饰。支持的函数返回值类型请参考[序列化支持类型](../../../../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。 |
| args | A | 是 | 任务执行传入函数的入参，支持的参数类型请参考[序列化支持类型](../../../../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。默认值为**undefined**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<R> | Promise对象，返回任务函数的执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: number): number {
  console.info("printArgs: " + args);
  return args;
}

@Concurrent
function testWithThreeParams(a: number, b: string, c: number): string {
  return b;
}

@Concurrent
function testWithArray(args: [number, string]): string {
  return "success";
}

taskpool.execute<[number], number>(printArgs, 100).then((value: number) => { // 100: test number
  console.info("taskpool result: " + value); // "taskpool result: 100"
});

taskpool.execute<[number, string, number], string>(testWithThreeParams, 100, "test", 100).then((value: string) => {
  console.info("taskpool result: " + value); // "taskpool result: test"
});

taskpool.execute<[[number, string]], string>(testWithArray, [100, "test"]).then((value: string) => {
  console.info("taskpool result: " + value); // "taskpool result: success"
});

```


## execute

```TypeScript
function execute(task: Task, priority?: Priority): Promise<Object>
```

将创建好的任务添加到taskpool的内部任务队列中，任务不会立即执行，而是等待分发到工作线程执行。当前模式支持设置任务优先级和通过cancel取消任务。任务不能是任务组任务、串行队列任务或异步队列任务。对于非长时任务，可以多次调用执行；对于长时任务，仅支持执行一次。使用Promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function execute(task: Task, priority?: Priority): Promise<Object>--><!--Device-taskpool-function execute(task: Task, priority?: Priority): Promise<Object>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | [Task](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-task-i.md) | 是 | 需要在任务池中执行的任务。 |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | 否 | 该参数表示等待执行的任务的优先级，默认值为**taskpool.Priority.MEDIUM**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<unknown> | <br>**适用版本：** 9 - 17 |
| Promise<Object> | Promise对象，返回任务函数的执行结果。<br>**适用版本：** 11+ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200003](../errorcode-utils.md#10200003-worker初始化失败) | Worker initialization failed.<br>**适用版本：** 9 - 17 |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |
| [10200051](../errorcode-utils.md#10200051-无法再次执行周期任务) | The periodic task cannot be executed again.<br>**适用版本：** 12+ |
| [10200057](../errorcode-utils.md#10200057-任务无法被两种api执行) | The task cannot be executed by two APIs.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: number): number {
    console.info("printArgs: " + args);
    return args;
}

let task1: taskpool.Task = new taskpool.Task(printArgs, 100); // 100: test number
let task2: taskpool.Task = new taskpool.Task(printArgs, 200); // 200: test number
let task3: taskpool.Task = new taskpool.Task(printArgs, 300); // 300: test number
taskpool.execute(task1, taskpool.Priority.LOW).then((value: Object) => {
  console.info("taskpool result1: " + value);
});
taskpool.execute(task2, taskpool.Priority.MEDIUM).then((value: Object) => {
  console.info("taskpool result2: " + value);
});
taskpool.execute(task3, taskpool.Priority.HIGH).then((value: Object) => {
  console.info("taskpool result3: " + value);
});

```


## execute

```TypeScript
function execute<A extends Array<Object>, R>(task: GenericsTask<A, R>, priority?: Priority): Promise<R>
```

将创建好的泛型任务放入taskpool的内部任务队列，校验任务的参数类型和返回值类型。使用Promise异步回调。execute任务的校验是结合**new GenericsTask**一起用的，参数、返回值类型需与**new GenericsTask**中的类型保持一致。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function execute<A extends Array<Object>, R>(task: GenericsTask<A, R>, priority?: Priority): Promise<R>--><!--Device-taskpool-function execute<A extends Array<Object>, R>(task: GenericsTask<A, R>, priority?: Priority): Promise<R>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | [GenericsTask](arkts-arkts-taskpool-genericstask-c.md)<A, R> | 是 | 需要在任务池中执行的泛型任务。 |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | 否 | 等待执行的任务的优先级，默认值为**taskpool.Priority.MEDIUM**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<R> | Promise对象，返回任务函数的执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |
| [10200051](../errorcode-utils.md#10200051-无法再次执行周期任务) | The periodic task cannot be executed again. |
| [10200057](../errorcode-utils.md#10200057-任务无法被两种api执行) | The task cannot be executed by two APIs.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: number): number {
    console.info("printArgs: " + args);
    return args;
}

let task1: taskpool.Task = new taskpool.GenericsTask<[number], number>(printArgs, 100); // 100: test number
let task2: taskpool.Task = new taskpool.GenericsTask<[number], number>(printArgs, 200); // 200: test number
let task3: taskpool.Task = new taskpool.GenericsTask<[number], number>(printArgs, 300); // 300: test number
taskpool.execute<[number], number>(task1, taskpool.Priority.LOW).then((value: number) => {
  console.info("taskpool result1: " + value);
});
taskpool.execute<[number], number>(task2, taskpool.Priority.MEDIUM).then((value: number) => {
  console.info("taskpool result2: " + value);
});
taskpool.execute<[number], number>(task3, taskpool.Priority.HIGH).then((value: number) => {
  console.info("taskpool result3: " + value);
});

```


## execute

```TypeScript
function execute(group: TaskGroup, priority?: Priority): Promise<Object[]>
```

将创建好的任务组放入taskpool内部任务队列，任务组中的任务不会立即执行，而是等待分发到工作线程执行。任务组中任务全部执行完成后，结果数组统一返回。此模式适用于执行关联任务。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function execute(group: TaskGroup, priority?: Priority): Promise<Object[]>--><!--Device-taskpool-function execute(group: TaskGroup, priority?: Priority): Promise<Object[]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| group | [TaskGroup](arkts-arkts-taskpool-taskgroup-c.md) | 是 | 需要在任务池中执行的任务组。 |
| priority | [Priority](arkts-arkts-taskpool-priority-e.md) | 否 | 等待执行的任务组的优先级，该参数默认值为**taskpool.Priority.MEDIUM**。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Object[]> | Promise对象数组，返回任务函数的执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200059](../errorcode-utils.md#10200059-任务组不能重复执行) | TaskGroup cannot be re-executed.<br>**适用版本：** 24+ |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: number): number {
    console.info("printArgs: " + args);
    return args;
}

let taskGroup1: taskpool.TaskGroup = new taskpool.TaskGroup();
taskGroup1.addTask(printArgs, 10); // 10: test number
taskGroup1.addTask(printArgs, 20); // 20: test number
taskGroup1.addTask(printArgs, 30); // 30: test number

let taskGroup2: taskpool.TaskGroup = new taskpool.TaskGroup();
let task1: taskpool.Task = new taskpool.Task(printArgs, 100); // 100: test number
let task2: taskpool.Task = new taskpool.Task(printArgs, 200); // 200: test number
let task3: taskpool.Task = new taskpool.Task(printArgs, 300); // 300: test number
taskGroup2.addTask(task1);
taskGroup2.addTask(task2);
taskGroup2.addTask(task3);
taskpool.execute(taskGroup1).then((res: Array<Object>) => {
  console.info("Succeeded in executing task, res is:" + res);
});
taskpool.execute(taskGroup2).then((res: Array<Object>) => {
  console.info("Succeeded in executing task, res is:" + res);
});

```


## execute

```TypeScript
function execute(task: Task, configs: Configs): Promise<Object>
```

通过Configs执行并发任务。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function execute(task: Task, configs: Configs): Promise<Object>--><!--Device-taskpool-function execute(task: Task, configs: Configs): Promise<Object>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | [Task](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-task-i.md) | 是 | 需要执行的任务。 |
| configs | [Configs](arkts-arkts-taskpool-configs-i.md) | 是 | 任务的配置项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Object> | @throws { BusinessError } 10200006 - An exception occurred during serialization. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |
| [10200051](../errorcode-utils.md#10200051-无法再次执行周期任务) | The periodic task cannot be executed again. |
| [10200057](../errorcode-utils.md#10200057-任务无法被两种api执行) | The task cannot be executed by two APIs. |
| [10200058](../errorcode-utils.md#10200058-任务执行超时) | Task timed out. |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: number, time: number): number {
  let start = Date.now();
  while (Date.now() - start < time) {
    continue;
  }
  return args;
}

let task: taskpool.Task = new taskpool.Task(printArgs, 100, 1000);
let config: taskpool.Configs = { timeout: 500, priority: taskpool.Priority.HIGH };
taskpool.execute(task, config).catch((e: BusinessError) => {
  // Failed to execute task. Code: 10200058, message: Task timed out.
  console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
})
try {
  taskpool.execute(task, { timeout: 500 });
} catch (e) {
  // Failed to execute task. Code: 10200057, message: The task cannot be executed by two APIs, the timeout task cannot be executed again.
  console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
}

```


## execute

```TypeScript
function execute<A extends Array<Object>, R>(task: GenericsTask<A, R>, configs: Configs): Promise<R>
```

通过Configs执行并发泛型任务。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function execute<A extends Array<Object>, R>(task: GenericsTask<A, R>, configs: Configs): Promise<R>--><!--Device-taskpool-function execute<A extends Array<Object>, R>(task: GenericsTask<A, R>, configs: Configs): Promise<R>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| task | [GenericsTask](arkts-arkts-taskpool-genericstask-c.md)<A, R> | 是 | 需要执行的泛型任务。 |
| configs | [Configs](arkts-arkts-taskpool-configs-i.md) | 是 | 任务的配置项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<R> | @throws { BusinessError } 10200006 - An exception occurred during serialization. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |
| [10200051](../errorcode-utils.md#10200051-无法再次执行周期任务) | The periodic task cannot be executed again. |
| [10200057](../errorcode-utils.md#10200057-任务无法被两种api执行) | The task cannot be executed by two APIs. |
| [10200058](../errorcode-utils.md#10200058-任务执行超时) | Task timed out. |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: number, time: number): number {
  let start = Date.now();
  while (Date.now() - start < time) {
    continue;
  }
  return args;
}

let task: taskpool.Task = new taskpool.GenericsTask<[number, number], number>(printArgs, 100, 1000);
let config: taskpool.Configs = { timeout: 500, priority: taskpool.Priority.MEDIUM };
taskpool.execute<[number, number], number>(task, config).catch((e: BusinessError) => {
  // Failed to execute task. Code: 10200058, message: Task timed out.
  console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
})
try {
  taskpool.execute<[number, number], number>(task, { timeout: 500 });
} catch (e) {
  // Failed to execute task. Code: 10200057, message: The task cannot be executed by two APIs, the timeout task cannot be executed again.
  console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
}

```


## execute

```TypeScript
function execute(group: TaskGroup, configs: Configs): Promise<Object[]>
```

通过Configs执行并发任务组。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-taskpool-function execute(group: TaskGroup, configs: Configs): Promise<Object[]>--><!--Device-taskpool-function execute(group: TaskGroup, configs: Configs): Promise<Object[]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| group | [TaskGroup](arkts-arkts-taskpool-taskgroup-c.md) | 是 | 需要执行的任务组。 |
| configs | [Configs](arkts-arkts-taskpool-configs-i.md) | 是 | 任务组中各任务的配置项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Object[]> | @throws { BusinessError } 10200006 - An exception occurred during serialization. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200059](../errorcode-utils.md#10200059-任务组不能重复执行) | TaskGroup cannot be re-executed. |
| [10200070](../errorcode-utils.md#10200070-任务组执行超时) | TaskGroup timed out. |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: number, time: number): number {
  let start = Date.now();
  while (Date.now() - start < time) {
    continue;
  }
  return args;
}

let taskGroup: taskpool.TaskGroup = new taskpool.TaskGroup();
taskGroup.addTask(printArgs, 10, 1000);
let config: taskpool.Configs = {timeout: 500, priority: taskpool.Priority.HIGH};
taskpool.execute(taskGroup, config).catch((e:BusinessError) => {
  // Failed to execute task. Code: 10200070, message: TaskGroup timed out.
  console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
})
try {
  taskpool.execute(taskGroup, config);
} catch (e) {
  // Failed to execute task. Code: 10200059, message: TaskGroup cannot be re-executed, taskGroup has already set timeout.
  console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
}

```

