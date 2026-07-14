# executePeriodically

## executePeriodically

```TypeScript
function executePeriodically(period: number, task: Task, priority?: Priority): void
```

周期任务每隔period时长执行一次。当前执行模式支持设置任务优先级，并可以通过调用**cancel()**取消执行。周期任务不能是任务组任务、
串行队列任务或异步队列任务，不能再次调用执行接口，且执行的任务不能拥有依赖关系。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| period | number | 是 | 周期时长，单位为ms。period值必须要大于等于0。该值应为整数。<br>单位：毫秒。 |
| task | Task | 是 | 需要周期执行的任务。 |
| priority | Priority | 否 | 周期执行的任务的优先级，该参数默认值为**taskpool.Priority.MEDIUM**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |
| [10200028](../errorcode-utils.md#10200028-延时时间小于零) | The period is less than zero. |
| [10200050](../errorcode-utils.md#10200050-并发任务已执行无法周期执行) | The concurrent task has been executed and cannot be executed periodically. |
| [10200057](../errorcode-utils.md#10200057-任务无法被两种api执行) | The task cannot be executed by two APIs.<br>**适用版本：** 18+ |

**示例：**

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
  taskpool.Task.sendData(args); // 向宿主线程发送消息
}

function printResult(data: number): void {
  console.info("taskpool: data is: " + data);
}

function taskpoolTest() {
  try {
    let task: taskpool.Task = new taskpool.Task(printArgs, 100); // 100: test number
    taskpool.executePeriodically(1000, task); // 1000: period is 1000ms
  } catch (e) {
    console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
  }

  try {
    let periodicTask: taskpool.Task = new taskpool.Task(testExecutePeriodically, 200); // 200: test number
    periodicTask.onReceiveData(printResult);
    taskpool.executePeriodically(1000, periodicTask); // 1000: period is 1000ms
  } catch (e) {
    console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
  }
}

taskpoolTest();

```


## executePeriodically

```TypeScript
function executePeriodically<A extends Array<Object>, R>(period: number, task: GenericsTask<A, R>, priority?: Priority): void
```

周期执行泛型任务，不校验任务的参数类型和返回值类型。
executePeriodically任务的校验是结合**new GenericsTask**一起用的，参数、返回值类型需与**new GenericsTask**中的类型保持一致。

**起始版本：** 13

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| period | number | 是 | 周期时长，单位为ms。period值必须要大于等于0。该值应为整数。<br>单位：毫秒。 |
| task | GenericsTask&lt;A, R&gt; | 是 | 需要周期执行的泛型任务。 |
| priority | Priority | 否 | 周期执行的任务的优先级，该参数默认值为**taskpool.Priority.MEDIUM**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |
| [10200028](../errorcode-utils.md#10200028-延时时间小于零) | The period is less than zero. |
| [10200050](../errorcode-utils.md#10200050-并发任务已执行无法周期执行) | The concurrent task has been executed and cannot be executed periodically. |
| [10200057](../errorcode-utils.md#10200057-任务无法被两种api执行) | The task cannot be executed by two APIs.<br>**适用版本：** 18+ |

**示例：**

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
  taskpool.Task.sendData(args); // 向宿主线程发送消息
}

function printResult(data: number): void {
  console.info("taskpool: data is: " + data);
}

function taskpoolTest() {
  try {
    let task: taskpool.Task = new taskpool.GenericsTask<[number], void>(printArgs, 100); // 100: test number
    taskpool.executePeriodically<[number], void>(1000, task); // 1000: period is 1000ms
  } catch (e) {
    console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
  }

  try {
    let periodicTask: taskpool.Task = new taskpool.GenericsTask<[number], void>(testExecutePeriodically, 200); // 200: test number
    periodicTask.onReceiveData(printResult);
    taskpool.executePeriodically<[number], void>(1000, periodicTask); // 1000: period is 1000ms
  } catch (e) {
    console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
  }
}

taskpoolTest();

```

