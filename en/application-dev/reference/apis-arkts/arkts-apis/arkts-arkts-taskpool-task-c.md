# Task

Enumerates tasks, which can be executed for multiple times, placed in a task group, serial queue, or asynchronous queue for execution, or added with dependencies for execution.

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { taskpool } from '@kit.ArkTS';
```

## addDependency

```TypeScript
addDependency(...tasks: Task[]): void
```

Adds dependent tasks for this task. Before using this API, you must create a **Task** instance. The task and its dependent tasks cannot be a task in a task group, serial queue, or asynchronous queue, a task that has been executed, or a periodic task. A task with a dependency relationship (a task that depends on another task or a task that is depended on) cannot be executed multiple times.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tasks | [Task](arkts-arkts-taskpool-task-c.md)[] | Yes | Array of tasks on which the current task depends. The default value is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200026](../errorcode-utils.md#10200026-task-with-a-cyclic-dependency) | There is a circular dependency. |
| [10200052](../errorcode-utils.md#10200052-periodic-task-cannot-have-dependencies) | The periodic task cannot have a dependency.<br>**Applicable version:** 12 and later |
| [10200056](../errorcode-utils.md#10200056-asynchronous-queue-task-cannot-have-dependencies) | The task has been executed by the AsyncRunner.<br>**Applicable version:** 18 and later |

**Examples**

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

## constructor

```TypeScript
constructor(func: Function, ...args: Object[])
```

A constructor used to create a **Task** instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| func | Function | Yes | Function to be executed. The function must be decorated using [@Concurrent](../../../arkts-utils/taskpool-introduction.md#concurrent-decorator). For details about the supported return value types of the function, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). |
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

let task: taskpool.Task = new taskpool.Task(printArgs, "this is my first Task");
```

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

## constructor

```TypeScript
constructor(name: string, func: Function, ...args: Object[])
```

A constructor used to create a **Task** instance, with the task name specified.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Task name. |
| func | Function | Yes | Function to be executed. The function must be decorated using [@Concurrent](../../../arkts-utils/taskpool-introduction.md#concurrent-decorator). For details about the supported return value types of the function, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). |
| args | Object[] | Yes | Arguments of the function. For details about the supported types, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). The default value is **undefined**. |

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

let task: taskpool.Task = new taskpool.Task(printArgs, "this is my first Task");
```

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

## isCanceled

```TypeScript
static isCanceled(): boolean
```

Checks whether the running task is canceled. Before using this method, you need to create a **Task** object.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | If the task is canceled, **true** is returned. Otherwise, **false** is returned. |

**Examples**

```TypeScript
@Concurrent
function inspectStatus(arg: number): number {
    // do something
    if (taskpool.Task.isCanceled()) {
      console.info("task has been canceled.");
      // do something
      return arg + 1;
    }
    // do something
    return arg;
}
```

```TypeScript
> NOTE
> 
> isCanceled must be used together with taskpool.cancel. If cancel is not called, isCanceled returns false by default.
```

## isDone

```TypeScript
isDone(): boolean
```

Checks whether the task is complete.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the task is complete; otherwise, **false** is returned. |

**Examples**

```TypeScript
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
    console.info("taskpool test result: " + res);
  }).catch((err: string) => {
    console.error("taskpool test occur error: " + err);
  });

  setTimeout(() => {
    if (!task.isDone()) {
      taskpool.cancel(task);
    }
  }, 3000); // Wait for 3s to ensure that the task has been executed.
}

taskpoolCancel();
```

## onEnqueued

```TypeScript
onEnqueued(callback: CallbackFunction): void
```

Register a callback function and call it when a task is enqueued. The registration must be carried out before the task is executed. Otherwise, an exception is thrown.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [CallbackFunction](arkts-arkts-taskpool-callbackfunction-t.md) | Yes | Callback function to register. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200034](../errorcode-utils.md#10200034-no-callback-function-is-registered-for-a-listening-task) | The executed task does not support the registration of listeners. |

**Examples**

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

## onExecutionFailed

```TypeScript
onExecutionFailed(callback: CallbackFunctionWithError): void
```

Register a callback function and call it when a task fails to be executed(Periodic tasks are not supported). The registration must be carried out before the task is executed. Otherwise, an exception is thrown.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [CallbackFunctionWithError](arkts-arkts-taskpool-callbackfunctionwitherror-t.md) | Yes | Callback function to register. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200034](../errorcode-utils.md#10200034-no-callback-function-is-registered-for-a-listening-task) | The executed task does not support the registration of listeners. |

**Examples**

```TypeScript
import { taskpool } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';
import { HashMap } from '@kit.ArkTS';

@Concurrent
function test(args: number) {
  let t = Date.now();
  while ((Date.now() - t) < 100) {
    continue;
  }
  let hashMap1: HashMap<string, number> = new HashMap();
  hashMap1.set('a', args);
  return hashMap1;
}

let task2 = new taskpool.Task(test, 1);
task2.onExecutionFailed((e: Error) => {
  console.info("taskpool: onExecutionFailed error is " + e);
})
taskpool.execute(task2).then(() => {
  console.info("taskpool: execute task success");
}).catch((e:BusinessError) => {
  console.error(`taskpool: error code: ${e.code}, error info: ${e.message}`);
})
```

## onExecutionSucceeded

```TypeScript
onExecutionSucceeded(callback: CallbackFunction): void
```

Register a callback function and call it when a task is executed successfully. The registration must be carried out before the task is executed. Otherwise, an exception is thrown.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [CallbackFunction](arkts-arkts-taskpool-callbackfunction-t.md) | Yes | Callback function to register. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200034](../errorcode-utils.md#10200034-no-callback-function-is-registered-for-a-listening-task) | The executed task does not support the registration of listeners. |

**Examples**

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

## onReceiveData

```TypeScript
onReceiveData(callback?: Function): void
```

Registers a callback for a task to receive and process data from the worker thread. Before using this API, you must create a Task instance. NOTE: If multiple callbacks are registered for the same task, only the last registration takes effect.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Function | No | Callback function for processing the data received. The data sent to the host thread is transferred to the callback as an input parameter. If no value is passed in, all the registered callbacks are canceled. |

**Examples**

```TypeScript
@Concurrent
function ConcurrentFunc(num: number): number {
  let res: number = num * 10;
  taskpool.Task.sendData(res);
  return num;
}

function printLog(data: number): void {
  console.info("taskpool: data is: " + data);
}

async function testFunc(): Promise<void> {
  try {
    let task: taskpool.Task = new taskpool.Task(ConcurrentFunc, 1);
    task.onReceiveData(printLog);
    await taskpool.execute(task);
  } catch (e) {
    console.error(`taskpool: error code: ${e.code}, info: ${e.message}`);
  }
}

testFunc();
```

## onStartExecution

```TypeScript
onStartExecution(callback: CallbackFunction): void
```

Register a callback function and call it when the execution of a task starts. The registration must be carried out before the task is executed. Otherwise, an exception is thrown.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [CallbackFunction](arkts-arkts-taskpool-callbackfunction-t.md) | Yes | Callback function to register. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200034](../errorcode-utils.md#10200034-no-callback-function-is-registered-for-a-listening-task) | The executed task does not support the registration of listeners. |

**Examples**

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

## removeDependency

```TypeScript
removeDependency(...tasks: Task[]): void
```

Removes dependent tasks for this task. Before using this method, you need to construct a **Task** object.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tasks | [Task](arkts-arkts-taskpool-task-c.md)[] | Yes | Array of tasks on which the current task depends. The default value is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200027](../errorcode-utils.md#10200027-dependency-does-not-exist) | The dependency does not exist. |
| [10200052](../errorcode-utils.md#10200052-periodic-task-cannot-have-dependencies) | The periodic task cannot have a dependency.<br>**Applicable version:** 12 and later |
| [10200056](../errorcode-utils.md#10200056-asynchronous-queue-task-cannot-have-dependencies) | The task has been executed by the AsyncRunner.<br>**Applicable version:** 18 and later |

**Examples**

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

## sendData

```TypeScript
static sendData(...args: Object[]): void
```

Sends data to the host thread and triggers the registered callback. Before calling this method, you need to construct a **Task** object.

> **NOTE:** 
> 
> - The API should be called in the TaskPool thread.
> 
> - Do not use this API in a callback function. Otherwise, messages may fail to be passed to the host thread.
> 
> - Do not use this API in an asynchronous function. Otherwise, messages may fail to be passed to the host thread. If this API is used in an asynchronous function, use **await** to ensure that the asynchronous function is executed synchronously in the task.
> 
> - Before calling this API, ensure that the callback function for processing data has been registered in the host thread.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| args | Object[] | Yes | Data to be used as the argument of the registered callback. For details about the supported parameter types, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). The default value is **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200006](../errorcode-utils.md#10200006-worker-data-serialization-exception) | An exception occurred during serialization. |
| [10200022](../errorcode-utils.md#10200022-functions-not-called-in-taskpool) | The function is not called in the TaskPool thread. |
| [10200023](../errorcode-utils.md#10200023-functions-not-called-in-concurrent-functions) | The function is not called in the concurrent function. |
| [10200024](../errorcode-utils.md#10200024-functions-not-registered-in-the-host-thread) | The callback is not registered on the host side. |

**Examples**

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
    console.error(`taskpool: error code: ${e.code}, info: ${e.message}`);
  }
}

taskpoolTest();
```

```TypeScript
// Call this method in an asynchronous function.
@Concurrent
async function sendDataTest(num: number) {
  let func = async () => {
    let asyncSleep = async (time: number): Promise<Object> => {
      return new Promise(resolve => setTimeout(resolve, time));
    }
    await asyncSleep(10000);
    let res: number = num * 10;
    taskpool.Task.sendData(res);
  }
  await func(); // Use await to ensure that the asynchronous function is executed synchronously in the task.
}

function taskpoolTest() {
  try {
    let task: taskpool.Task = new taskpool.Task(sendDataTest, 10);
    task.onReceiveData((data: string) => {
      console.info("taskpool: data is: " + data);
    });
    taskpool.execute(task);
  } catch (e) {
    console.error(`taskpool: error code: ${e.code}, info: ${e.message}`);
  }
}

taskpoolTest();
```

## setCloneList

```TypeScript
setCloneList(cloneList: Object[] | ArrayBuffer[]): void
```

Sets the task clone list. Before using this method, you need to construct a **Task** object.

> **NOTE:** 
> 
> This API must be used together with the
> [@Sendable decorator](../../../arkts-utils/arkts-sendable.md#sendable-decorator). Otherwise, an exception is
> thrown. You are advised to use this decorator to avoid exceptions.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cloneList | Object[] &#124; ArrayBuffer[] | Yes | The type of the passed-in array must be [sendable data types](../../../arkts-utils/arkts-sendable.md#sendable-data-types) or ArrayBuffer.<br>- All [Sendable class](../../../arkts-utils/arkts-sendable.md#sendable-class) instances or ArrayBuffer objects passed in to **cloneList** are transferred in copy mode between threads. This means that any modification to the destination objects does not affect the original objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200029](../errorcode-utils.md#10200029-arraybuffer-cannot-be-set-as-both-transferlist-and-clonelist) | An ArrayBuffer cannot be set as both a transfer list and a clone list. |

**Examples**

```TypeScript
// sendable.ets
// Define two Sendable classes: BaseClass and its child class DeriveClass.
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
// The host thread (UI main thread) calls the methods of BaseClass and DeriveClass in the task pool thread and accesses their properties.
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
  // Obtain the result of the item specified by num from Fibonacci sequence.
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
          // task1 calls BaseClass.str1/BaseClass.SetNum/BaseClass.GetNum/BaseClass.isDone1/BaseClass.publicFunc.
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

          // task2 calls DeriveClass.printName.
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

## setTransferList

```TypeScript
setTransferList(transfer?: ArrayBuffer[]): void
```

Sets the task transfer list. Before using this API, you must create a **Task** instance. If this API is not called, the ArrayBuffer in the data is transferred by default.

> **NOTE:** 
> 
> This API is used to set the task transfer list in the form of **ArrayBuffer** in the task pool. The
> **ArrayBuffer** instance does not copy the content in the task to the worker thread during transfer. Instead,
> it transfers the buffer control right to the worker thread. After the transfer, the **ArrayBuffer** instance
> becomes invalid. An empty **ArrayBuffer** will not be transferred.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transfer | ArrayBuffer[] | No | **ArrayBuffer** instance holding the objects to transfer. The default value is an empty array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200029](../errorcode-utils.md#10200029-arraybuffer-cannot-be-set-as-both-transferlist-and-clonelist) | An ArrayBuffer cannot be set as both a transfer list and a clone list.<br>**Applicable version:** 11 and later |

**Examples**

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
// The execution result is as follows:
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
// The value is 0 after transfer. The execution result is as follows:
// testTransfer view2 byteLength: 0
// testTransfer view3 byteLength: 0
```

## arguments

```TypeScript
arguments?: Object[]
```

Arguments of the function. For details about the supported parameter types, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types).<br> This API can be used in atomic services since API version 11.

**Type:** Object[]

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## cpuDuration

```TypeScript
cpuDuration: number
```

CPU time of the task. in ms. You are advised not to change the value.<br> This API can be used in atomic services since API version 11.

**Type:** number

**Default:** 0

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## function

```TypeScript
function: Function
```

Function to be passed in during task creation. For details about the supported return value types of the function, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types).<br> This API can be used in atomic services since API version 11.

**Type:** Function

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## ioDuration

```TypeScript
ioDuration: number
```

Asynchronous I/O time of the task. in ms. You are advised not to change the value.<br> This API can be used in atomic services since API version 11.

**Type:** number

**Default:** 0

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## name

```TypeScript
name: string
```

Name of the task specified when the task is created. You are advised not to change the value.<br> This API can be used in atomic services since API version 11.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## taskId

```TypeScript
taskId: number
```

Task ID, which is globally unique by default. You are advised not to change the value.<br> This API can be used in atomic services since API version 18.

**Type:** number

**Default:** 0

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

## totalDuration

```TypeScript
totalDuration: number
```

Total execution time of the task. in ms. You are advised not to change the value.<br> This API can be used in atomic services since API version 11.

**Type:** number

**Default:** 0

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
