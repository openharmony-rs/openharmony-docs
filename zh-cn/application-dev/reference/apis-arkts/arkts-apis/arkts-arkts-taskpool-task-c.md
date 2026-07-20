# Task

表示任务。任务可以多次执行，也可以放入任务组、串行队列或异步队列执行，还支持添加依赖关系。

**起始版本：** 9

<!--Device-taskpool-class Task--><!--Device-taskpool-class Task-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

<a id="adddependency"></a>
## addDependency

```TypeScript
addDependency(...tasks: Task[]): void
```

为当前任务添加对其他任务的依赖。使用该方法前需先构造**Task**实例。该任务和被依赖的任务不能是任务组任务、串行队列任务、异步队列任务、已执行任务或周期任务。存在依赖关系的任务（依赖其他任务的任务或被依赖的任务）执行后不可再次执行。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-addDependency(...tasks: Task[]): void--><!--Device-Task-addDependency(...tasks: Task[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tasks | [Task](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-task-i.md)[] | 是 | 被依赖的任务数组。默认值为**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200026](../errorcode-utils.md#10200026-当前任务存在循环依赖) | There is a circular dependency. |
| [10200052](../errorcode-utils.md#10200052-周期性任务不能具有依赖项) | The periodic task cannot have a dependency.<br>**适用版本：** 12+ |
| [10200056](../errorcode-utils.md#10200056-任务已被asyncrunner执行) | The task has been executed by the AsyncRunner.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
@Concurrent
function delay(args: number): number {
  let t: number = Date.now();
  while ((Date.now() - t) < 1000) {
    continue;
  }
  return args;
}

let task1:taskpool.Task = new taskpool.Task(delay, 100);
let task2:taskpool.Task = new taskpool.Task(delay, 200);
let task3:taskpool.Task = new taskpool.Task(delay, 200);

console.info("dependency: add dependency start");
task1.addDependency(task2);
task2.addDependency(task3);
console.info("dependency: add dependency end");

console.info("dependency: start execute second");
taskpool.execute(task1).then(() => {
  console.info("dependency: second task1 success");
})
taskpool.execute(task2).then(() => {
  console.info("dependency: second task2 success");
})
taskpool.execute(task3).then(() => {
  console.info("dependency: second task3 success");
})

```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(func: Function, ...args: Object[])
```

Task的构造函数，用于创建一个**Task**实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-constructor(func: Function, ...args: Object[])--><!--Device-Task-constructor(func: Function, ...args: Object[])-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| func | Function | 是 | 执行的逻辑需要传入函数，该函数必须使用[@Concurrent装饰器](docroot://arkts-utils/taskpool-introduction.md#concurrent装饰器)装饰。支持的函数返回值类型请参考[序列化支持类型](docroot://reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。 |
| args | Object[] | 是 | 任务执行传入函数的入参，支持的参数类型请参考[序列化支持类型](docroot://reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。默认值为**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: string): string {
  console.info("printArgs: " + args);
  return args;
}

let task: taskpool.Task = new taskpool.Task(printArgs, "this is my first Task");

```

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor(name: string, func: Function, ...args: Object[])
```

Task的构造函数用于创建一个**Task**实例，并可指定任务名称。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-constructor(name: string, func: Function, ...args: Object[])--><!--Device-Task-constructor(name: string, func: Function, ...args: Object[])-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 任务名称。 |
| func | Function | 是 | 执行的逻辑需要传入函数，该函数必须使用[@Concurrent装饰器](docroot://arkts-utils/taskpool-introduction.md#concurrent装饰器)装饰。支持的函数返回值类型请参考[序列化支持类型](docroot://reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。 |
| args | Object[] | 是 | 任务执行传入函数的入参，支持的类型请参考[序列化支持类型](docroot://reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。默认值为**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200014](../errorcode-utils.md#10200014-非concurrent函数错误) | The function is not marked as concurrent. |

**示例：**

```TypeScript
@Concurrent
function printArgs(args: string): string {
  console.info("printArgs: " + args);
  return args;
}

let taskName: string = "taskName";
let task: taskpool.Task = new taskpool.Task(taskName, printArgs, "this is my first Task");
let name: string = task.name;

```

<a id="iscanceled"></a>
## isCanceled

```TypeScript
static isCanceled(): boolean
```

检查当前正在运行的任务是否已取消。使用此方法前，需要先创建一个**Task**对象。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-static isCanceled(): boolean--><!--Device-Task-static isCanceled(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果当前正在运行的任务被取消返回**true**，否则返回**false**。 |

**示例：**

```TypeScript
@Concurrent
function inspectStatus(arg: number): number {
    // ...
    if (taskpool.Task.isCanceled()) {
      console.info("task has been canceled.");
      // ...
      return arg + 1;
    }
    // ...
    return arg;
}

```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

@Concurrent
function inspectStatus(arg: number): number {
  // 第一次检查任务是否已经取消并作出响应
  if (taskpool.Task.isCanceled()) {
    console.info("task has been canceled before 2s sleep.");
    return arg + 2;
  }
  // 延时2s
  let t: number = Date.now();
  while (Date.now() - t < 2000) {
    continue;
  }
  // 第二次检查任务是否已经取消并作出响应
  if (taskpool.Task.isCanceled()) {
    console.info("task has been canceled after 2s sleep.");
    return arg + 3;
  }
  return arg + 1;
}

let task: taskpool.Task = new taskpool.Task(inspectStatus, 100); // 100: test number
taskpool.execute(task).then((res: Object) => {
  console.info("Succeeded in executing task, result: " + res);
}).catch((e: BusinessError) => {
  console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
});
// 不调用cancel，isCanceled()默认返回false，task执行的结果为101

```

<a id="isdone"></a>
## isDone

```TypeScript
isDone(): boolean
```

检查任务是否已完成。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Task-isDone(): boolean--><!--Device-Task-isDone(): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果。任务执行完成时返回**true**，任务未执行完成时返回**false**。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

@Concurrent
function inspectStatus(arg: number): number {
  // 1s sleep
  let t: number = Date.now();
  while (Date.now() - t < 1000) {
    continue;
  }
  return arg + 1;
}

async function taskpoolCancel(): Promise<void> {
  let task: taskpool.Task = new taskpool.Task(inspectStatus, 100); // 100: test number
  taskpool.execute(task).then((res: Object) => {
    console.info("Succeeded in executing task, result: " + res);
  }).catch((e: BusinessError) => {
    console.error(`Failed to execute task. Code: ${e.code}, message: ${e.message}`);
  });

  setTimeout(() => {
    if (!task.isDone()) {
      taskpool.cancel(task);
    }
  }, 3000); // 延时3s，确保任务已执行
}

taskpoolCancel();

```

<a id="onenqueued"></a>
## onEnqueued

```TypeScript
onEnqueued(callback: CallbackFunction): void
```

注册回调函数，任务入队时将调用该函数。该注册需在任务执行前完成，否则会抛出异常。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Task-onEnqueued(callback: CallbackFunction): void--><!--Device-Task-onEnqueued(callback: CallbackFunction): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [CallbackFunction](arkts-arkts-taskpool-callbackfunction-t.md) | 是 | 需注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200034](../errorcode-utils.md#10200034-已执行的任务不支持注册监听器) | The executed task does not support the registration of listeners. |

**示例：**

```TypeScript
import { taskpool } from '@kit.ArkTS';

@Concurrent
function delay(args: number): number {
  let t: number = Date.now();
  while ((Date.now() - t) < 1000) {
    continue;
  }
  return args;
}

let task: taskpool.Task = new taskpool.Task(delay, 1);
task.onEnqueued(() => {
  console.info("taskpool: onEnqueued");
});
taskpool.execute(task).then(() => {
  console.info("taskpool: execute task success");
});

```

<a id="onexecutionfailed"></a>
## onExecutionFailed

```TypeScript
onExecutionFailed(callback: CallbackFunctionWithError): void
```

注册一个回调函数，并在任务执行失败时调用它（周期任务不支持）。该注册需在任务执行前完成，否则会抛出异常。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Task-onExecutionFailed(callback: CallbackFunctionWithError): void--><!--Device-Task-onExecutionFailed(callback: CallbackFunctionWithError): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [CallbackFunctionWithError](arkts-arkts-taskpool-callbackfunctionwitherror-t.md) | 是 | 需注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200034](../errorcode-utils.md#10200034-已执行的任务不支持注册监听器) | The executed task does not support the registration of listeners. |

**示例：**

```TypeScript
import { taskpool } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';
import { HashMap } from '@kit.ArkTS';

@Concurrent
function hashMapFunc(args: number) {
  let t = Date.now();
  while ((Date.now() - t) < 100) {
    continue;
  }
  return () => {};
}

let task2 = new taskpool.Task(hashMapFunc, 1);
task2.onExecutionFailed((e: Error) => {
  console.error("taskpool: onExecutionFailed error is " + e.message);
})
taskpool.execute(task2).then(() => {
  console.info("taskpool: execute task success");
}).catch((e:BusinessError) => {
  console.error(`taskpool: error code: ${e.code}, error message: ${e.message}`);
})

```

<a id="onexecutionsucceeded"></a>
## onExecutionSucceeded

```TypeScript
onExecutionSucceeded(callback: CallbackFunction): void
```

注册一个回调函数，并在任务执行成功时调用它。该注册需在任务执行前完成，否则会抛出异常。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Task-onExecutionSucceeded(callback: CallbackFunction): void--><!--Device-Task-onExecutionSucceeded(callback: CallbackFunction): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [CallbackFunction](arkts-arkts-taskpool-callbackfunction-t.md) | 是 | 需注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200034](../errorcode-utils.md#10200034-已执行的任务不支持注册监听器) | The executed task does not support the registration of listeners. |

**示例：**

```TypeScript
import { taskpool } from '@kit.ArkTS';

@Concurrent
function delay(args: number): number {
  let t: number = Date.now();
  while ((Date.now() - t) < 1000) {
    continue;
  }
  return args;
}

let task: taskpool.Task = new taskpool.Task(delay, 1);
task.onExecutionSucceeded(() => {
  console.info("taskpool: onExecutionSucceeded");
});
taskpool.execute(task).then(() => {
  console.info("taskpool: execute task success");
});

```

<a id="onreceivedata"></a>
## onReceiveData

```TypeScript
onReceiveData(callback?: Function): void
```

为任务注册回调函数，接收并处理任务池工作线程的数据。使用此方法前，需构造Task实例。说明：不支持为同一任务定义多种回调函数。如果多次赋值，只有最后一次赋值的回调函数会生效。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-onReceiveData(callback?: Function): void--><!--Device-Task-onReceiveData(callback?: Function): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Function | 否 | 处理数据的回调函数，发送到宿主线程的数据将会作为入参传入该回调函数。不传参可以取消注册的回调函数。 |

**示例：**

```TypeScript
@Concurrent
function concurrentFunc(num: number): number {
  let res: number = num * 10;
  taskpool.Task.sendData(res);
  return num;
}

function printLog(data: number): void {
  console.info("taskpool: data is: " + data);
}

async function testFunc(): Promise<void> {
  try {
    let task: taskpool.Task = new taskpool.Task(concurrentFunc, 1);
    task.onReceiveData(printLog);
    await taskpool.execute(task);
  } catch (e) {
    console.error(`taskpool: error code: ${e.code}, message: ${e.message}`);
  }
}

testFunc();

```

<a id="onstartexecution"></a>
## onStartExecution

```TypeScript
onStartExecution(callback: CallbackFunction): void
```

注册回调函数，任务执行前将调用该函数。该注册需在任务执行前完成，否则会抛出异常。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Task-onStartExecution(callback: CallbackFunction): void--><!--Device-Task-onStartExecution(callback: CallbackFunction): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [CallbackFunction](arkts-arkts-taskpool-callbackfunction-t.md) | 是 | 需注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200034](../errorcode-utils.md#10200034-已执行的任务不支持注册监听器) | The executed task does not support the registration of listeners. |

**示例：**

```TypeScript
import { taskpool } from '@kit.ArkTS';

@Concurrent
function delay(args: number): number {
  let t: number = Date.now();
  while ((Date.now() - t) < 1000) {
    continue;
  }
  return args;
}

let task: taskpool.Task = new taskpool.Task(delay, 1);
task.onStartExecution(() => {
  console.info("taskpool: onStartExecution");
});
taskpool.execute(task).then(() => {
  console.info("taskpool: execute task success");
});

```

<a id="removedependency"></a>
## removeDependency

```TypeScript
removeDependency(...tasks: Task[]): void
```

删除当前任务对其他任务的依赖。在使用该方法之前，需要先构造**Task**对象。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-removeDependency(...tasks: Task[]): void--><!--Device-Task-removeDependency(...tasks: Task[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tasks | [Task](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-agent-task-i.md)[] | 是 | 被依赖的任务数组。默认值为**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200027](../errorcode-utils.md#10200027-依赖关系不存在) | The dependency does not exist. |
| [10200052](../errorcode-utils.md#10200052-周期性任务不能具有依赖项) | The periodic task cannot have a dependency.<br>**适用版本：** 12+ |
| [10200056](../errorcode-utils.md#10200056-任务已被asyncrunner执行) | The task has been executed by the AsyncRunner.<br>**适用版本：** 18+ |

**示例：**

```TypeScript
@Concurrent
function delay(args: number): number {
  let t: number = Date.now();
  while ((Date.now() - t) < 1000) {
    continue;
  }
  return args;
}

let task1:taskpool.Task = new taskpool.Task(delay, 100);
let task2:taskpool.Task = new taskpool.Task(delay, 200);
let task3:taskpool.Task = new taskpool.Task(delay, 200);

console.info("dependency: add dependency start");
task1.addDependency(task2);
task2.addDependency(task3);
console.info("dependency: add dependency end");
console.info("dependency: remove dependency start");
task1.removeDependency(task2);
task2.removeDependency(task3);
console.info("dependency: remove dependency end");

console.info("dependency: start execute");
taskpool.execute(task1).then(() => {
  console.info("dependency: task1 success");
})
taskpool.execute(task2).then(() => {
  console.info("dependency: task2 success");
})
taskpool.execute(task3).then(() => {
  console.info("dependency: task3 success");
})

```

<a id="senddata"></a>
## sendData

```TypeScript
static sendData(...args: Object[]): void
```

任务执行过程中向宿主线程发送消息并触发已注册的回调函数。使用此方法前需构造**Task**对象。

> **说明**  
>  
> - 该接口应在taskpool的线程中调用。  
>  
> - 避免在回调函数中调用该方法，否则可能导致消息无法传递到宿主线程。  
>  
> - 避免在异步函数中调用该方法，否则可能导致消息无法传递到宿主线程。如果在异步函数中使用，  
> 则需要使用**await**来确保该异步函数在任务中同步执行完成。  
>  
> - 调用该接口时，请确保处理数据的回调函数已在宿主线程注册。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-static sendData(...args: Object[]): void--><!--Device-Task-static sendData(...args: Object[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| args | Object[] | 是 | 作为已注册回调函数入参的数据，支持的参数类型请参考[序列化支持类型](docroot://reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。默认值为**undefined**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker传输信息序列化异常) | An exception occurred during serialization. |
| [10200022](../errorcode-utils.md#10200022-未在任务池中调用的函数) | The function is not called in the TaskPool thread. |
| [10200023](../errorcode-utils.md#10200023-未在并发函数中调用的函数) | The function is not called in the concurrent function. |
| [10200024](../errorcode-utils.md#10200024-未在宿主线程中注册的函数) | The callback is not registered on the host side. |

**示例：**

```TypeScript
@Concurrent
function sendDataTest(num: number): number {
  let res: number = num * 10;
  taskpool.Task.sendData(res);
  return num;
}

function printLog(data: number): void {
  console.info("taskpool: data is: " + data);
}

async function taskpoolTest(): Promise<void> {
  try {
    let task: taskpool.Task = new taskpool.Task(sendDataTest, 1);
    task.onReceiveData(printLog);
    await taskpool.execute(task);
  } catch (e) {
    console.error(`taskpool: error code: ${e.code}, message: ${e.message}`);
  }
}

taskpoolTest();

```

```TypeScript
// 异步函数中调用该方法
@Concurrent
async function sendDataTest(num: number) {
  let asyncSleepAndSendData = async () => {
    let asyncSleep = async (time: number): Promise<Object> => {
      return new Promise(resolve => setTimeout(resolve, time));
    }
    await asyncSleep(10000);
    let res: number = num * 10;
    taskpool.Task.sendData(res);
  }
  await asyncSleepAndSendData(); // 需要使用await来确保该异步函数在任务中同步执行完成。
}

function taskpoolTest() {
  try {
    let task: taskpool.Task = new taskpool.Task(sendDataTest, 10);
    task.onReceiveData((data: number) => {
      console.info("taskpool: data is: " + data);
    });
    taskpool.execute(task);
  } catch (e) {
    console.error(`taskpool: error code: ${e.code}, info: ${e.message}`);
  }
}

taskpoolTest();

```

<a id="setclonelist"></a>
## setCloneList

```TypeScript
setCloneList(cloneList: Object[] | ArrayBuffer[]): void
```

设置任务的拷贝列表。在使用该方法前，需先构造**Task**对象。

> **说明**  
>  
> 该接口需搭配  
> [@Sendable装饰器](docroot://arkts-utils/arkts-sendable.md#sendable装饰器)使用，否则会抛异常。建议开发者使用该装饰器以避免异常。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-setCloneList(cloneList: Object[] | ArrayBuffer[]): void--><!--Device-Task-setCloneList(cloneList: Object[] | ArrayBuffer[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cloneList | Object[] \| ArrayBuffer[] | 是 | - 传入数组的类型必须为[Sendable支持的数据类型](docroot://arkts-utils/arkts-sendable.md#sendable支持的数据类型)或ArrayBuffer。<br>- 所有传入**cloneList**的[Sendable class](docroot://arkts-utils/arkts-sendable.md#sendable-class)实例或ArrayBuffer类型对象，在线程间传输的行为都会变成拷贝传递，即修改传输后的对象不会对原有对象产生任何影响。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200029](../errorcode-utils.md#10200029-无法将arraybuffer同时设置为transferlist和clonelist) | An ArrayBuffer cannot be set as both a transfer list and a clone list. |

**示例：**

```TypeScript
// sendable.ets
// 定义两个Sendable class：BaseClass及其子类DeriveClass
@Sendable
export class BaseClass {
  private str: string = "sendable: BaseClass";
  static num :number = 10;
  str1: string = "sendable: this is BaseClass's string";
  num1: number = 5;
  isDone1: boolean = false;

  private fibonacciRecursive(n: number): number {
    if (n <= 1) {
      return n;
    } else {
      return this.fibonacciRecursive(n - 1) + this.fibonacciRecursive(n - 2);
    }
  }

  private privateFunc(num: number): number{
    let res: number = this.fibonacciRecursive(num);
    console.info("sendable: BaseClass privateFunc res is: " + res);
    return res;
  }

  publicFunc(num: number): number {
    return this.privateFunc(num);
  }

  get GetNum(): number {
    return this.num1;
  }
  set SetNum(num: number) {
    this.num1 = num;
  }

  constructor() {
    console.info(this.str);
    this.isDone1 = true;
  }
}

@Sendable
export class DeriveClass extends BaseClass {
  name: string = "sendable: this is DeriveClass";
  printName() {
    console.info(this.name);
  }
  constructor() {
    super();
  }
}

```

```TypeScript
// index.ets
// 宿主线程（这里的宿主线程为UI主线程）调用taskpool，在taskpool线程中调用BaseClass和DeriveClass的方法、访问对应属性
import { taskpool } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';
import { BaseClass, DeriveClass } from './sendable';

@Concurrent
function testFunc(arr: Array<BaseClass>, num: number): number {
  let baseInstance1 = arr[0];
  console.info("sendable: str1 is: " + baseInstance1.str1);
  baseInstance1.SetNum = 100;
  console.info("sendable: num1 is: " + baseInstance1.GetNum);
  console.info("sendable: isDone1 is: " + baseInstance1.isDone1);
  // 获取斐波那契数列第num项的结果
  let res: number = baseInstance1.publicFunc(num);
  return res;
}

@Concurrent
function printLog(arr: Array<DeriveClass>): void {
  let deriveInstance = arr[0];
  deriveInstance.printName();
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text("TaskPool Test");
        }.onClick(() => {
          // task1访问调用BaseClass.str1/BaseClass.SetNum/BaseClass.GetNum/BaseClass.isDone1/BaseClass.publicFunc
          let baseInstance1: BaseClass = new BaseClass();
          let array1 = new Array<BaseClass>();
          array1.push(baseInstance1);
          let task1 = new taskpool.Task(testFunc, array1, 10);
          task1.setCloneList(array1);
          taskpool.execute(task1).then((res: Object) => {
            console.info("sendable: task1 res is: " + res);
          }).catch((e:BusinessError) => {
            console.error(`sendable: task1 execute Code is ${e.code}, message is ${e.message}`);
          })

          // task2调用DeriveClass.printName
          let deriveInstance: DeriveClass = new DeriveClass();
          let array2 = new Array<DeriveClass>();
          array2.push(deriveInstance);
          let task2 = new taskpool.Task(printLog, array2);
          task2.setCloneList(array2);
          taskpool.execute(task2).then(() => {
            console.info("sendable: task2 execute success");
          }).catch((e:BusinessError) => {
            console.error(`sendable: task2 execute Code is ${e.code}, message is ${e.message}`);
          })
        })
        .height('15%')
        .width('30%')
      }
      .width('100%')
    }
    .height('100%')
  }
}

```

<a id="settransferlist"></a>
## setTransferList

```TypeScript
setTransferList(transfer?: ArrayBuffer[]): void
```

设置任务的传输列表。使用该方法前需要先构造**Task**。不调用该接口，则传给任务的数据中的ArrayBuffer默认transfer转移。

> **说明**  
>  
> 此接口可以设置任务池中ArrayBuffer的transfer列表，transfer列表中的ArrayBuffer对象在传输时不会复制buffer内容到工作线程，  
> 而是转移buffer控制权至工作线程，传输后当前的ArrayBuffer失效。若ArrayBuffer为空，则不会transfer转移。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-setTransferList(transfer?: ArrayBuffer[]): void--><!--Device-Task-setTransferList(transfer?: ArrayBuffer[]): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transfer | ArrayBuffer[] | 否 | 可传输对象是ArrayBuffer的实例对象，默认为空数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200029](../errorcode-utils.md#10200029-无法将arraybuffer同时设置为transferlist和clonelist) | An ArrayBuffer cannot be set as both a transfer list and a clone list.<br>**适用版本：** 11+ |

**示例：**

```TypeScript
@Concurrent
function testTransfer(arg1: ArrayBuffer, arg2: ArrayBuffer): number {
  console.info("testTransfer arg1 byteLength: " + arg1.byteLength);
  console.info("testTransfer arg2 byteLength: " + arg2.byteLength);
  return 100;
}

let buffer: ArrayBuffer = new ArrayBuffer(8);
let view: Uint8Array = new Uint8Array(buffer);
let buffer1: ArrayBuffer = new ArrayBuffer(16);
let view1: Uint8Array = new Uint8Array(buffer1);

console.info("testTransfer view byteLength: " + view.byteLength);
console.info("testTransfer view1 byteLength: " + view1.byteLength);
// 执行结果为：
// testTransfer view byteLength: 8
// testTransfer view1 byteLength: 16

let task: taskpool.Task = new taskpool.Task(testTransfer, view, view1);
task.setTransferList([view.buffer, view1.buffer]);
taskpool.execute(task).then((res: Object) => {
  console.info("test result: " + res);
}).catch((e: string) => {
  console.error("test catch: " + e);
})
console.info("testTransfer view2 byteLength: " + view.byteLength);
console.info("testTransfer view3 byteLength: " + view1.byteLength);
// 经过transfer转移之后值为0，执行结果为：
// testTransfer view2 byteLength: 0
// testTransfer view3 byteLength: 0

```

## arguments

```TypeScript
arguments?: Object[]
```

创建任务传入函数所需的参数，支持的参数类型请参考[序列化支持类型](docroot://reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。<br>从API version 11开始，该接口支持在原子化服务中使用。

**类型：** Object[]

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-arguments?: Object[]--><!--Device-Task-arguments?: Object[]-End-->

**系统能力：** SystemCapability.Utils.Lang

## cpuDuration

```TypeScript
cpuDuration: number
```

执行任务CPU耗时。单位为ms。不建议修改此值。<br>从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**默认值：** 0

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-cpuDuration: number--><!--Device-Task-cpuDuration: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## function

```TypeScript
function: Function
```

创建任务时需要传入的函数，支持的函数返回值类型请参考[序列化支持类型](docroot://reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)。<br>从API version 11开始，该接口支持在原子化服务中使用。

**类型：** Function

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-function: Function--><!--Device-Task-function: Function-End-->

**系统能力：** SystemCapability.Utils.Lang

## ioDuration

```TypeScript
ioDuration: number
```

执行任务异步IO耗时。单位为ms。不建议修改此值。<br>从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**默认值：** 0

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-ioDuration: number--><!--Device-Task-ioDuration: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## name

```TypeScript
name: string
```

创建任务时指定的任务名称。不建议修改此值。<br>从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-name: string--><!--Device-Task-name: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## taskId

```TypeScript
taskId: number
```

任务ID。任务的标识符，系统默认提供全局唯一值，不建议修改此值。<br>从API version 18开始，该接口支持在原子化服务中使用。

**类型：** number

**默认值：** 0

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Task-taskId: number--><!--Device-Task-taskId: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## totalDuration

```TypeScript
totalDuration: number
```

执行任务总耗时。单位为ms。不建议修改此值。<br>从API version 11开始，该接口支持在原子化服务中使用。

**类型：** number

**默认值：** 0

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Task-totalDuration: number--><!--Device-Task-totalDuration: number-End-->

**系统能力：** SystemCapability.Utils.Lang

