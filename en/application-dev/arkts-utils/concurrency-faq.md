---
kits: ["ArkTS / Ark Programming Language"]
description: "A collection of common concurrency development issues and troubleshooting guidance: covering the troubleshooting directions for TaskPool tasks not executing, slow task execution, and serialization failures, as well as issues such as Sendable object instanceof judgment failure, property type inconsistency and new property exceptions, and the implementation principles of Promise."
keywords: [common concurrency issues, TaskPool task not executing, slow task execution troubleshooting, serialization failure, instanceof judgment, Sendable exception, Promise principle]
doctype: faq
status: active
---

# Common Concurrency Issues
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:30:17.289Z pushedAt=2026-11-12T02:56:51.314Z nl=1 -->

## Troubleshooting for Non-Executing Tasks in the TaskPool

If a task in a TaskPool is not executed, perform the following steps to quickly locate the fault:

1. Check whether the **taskpool.execute** API is called.

   When **taskpool.execute** is called, hilog prints a TaskPool call state log (Task Allocation: taskId:).

   If this log is missing, **taskpool.execute** is not actually called. Check whether the service logic preceding this API has been completed.

   <!-- @[is_execute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/IsExecute.ets) -->  
   
   ``` TypeScript
   import { taskpool } from '@kit.ArkTS';
   
   @Concurrent
   function createTask(a: number, b: number): number {
     let sum = a + b;
     return sum;
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
             .onClick(() => {
               console.info(`test start`);
               // Other business logic.
               // ...
               let task: taskpool.Task = new taskpool.Task(createTask, 1, 2);
               taskpool.execute(task);
               // ...
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   
   // If "test start" is printed in the console but the "Task Allocation: taskId:" log does not appear, taskpool.execute is not executed. Check other business logic in the application.
   ```


2. Check whether the task in the TaskPool is executed.

   Calling the **taskpool.execute** API will print a call state log **Task Allocation: taskId:**. 

   **The log output format may differ from the example. Focus on the taskId parameter in the log information.**
   
   After locating the Task Allocation: taskId log corresponding to the target task, search the log for the Id number following Task Allocation:. Under normal circumstances, the **execution state log** (Task Perform: name) and the **end state log** (Task PerformTask End: taskId) are printed.

   1.  If the call state log exists but the execution state log is missing, it may be because a preceding task has blocked the worker thread of the TaskPool, rendering it unavailable for subsequent tasks to execute. You should check the service logic or use trace to further pinpoint the issue.

   2. If the call state log and execution state log exist but the end state log is missing, check whether there are blocking operations in the service logic of the custom TaskPool task.

   3. If there is a significant time gap between the call state log and the execution state log, and your application is concerned about the timing of task execution, continue the analysis as follows:

      1. Check whether a large number of TaskPool tasks have accumulated and are not executing. If a large number of tasks are executed within a short period (resulting in a large number of call state logs), later tasks must wait for preceding tasks to finish. In this case, check the TaskPool scaling status. If the number of TaskPool worker threads has already scaled up to near the upper limit before the call state log is printed (the upper limit is the maxNum value in log fragment log2), it may be caused by too many tasks within a short period. The application can prioritize important tasks and time-sensitive tasks by setting priorities appropriately.

      2. Check whether the preceding tasks in the TaskPool are inherently time-consuming or have experienced blocking. If the preceding tasks are time-consuming, your application should address this by setting appropriate priorities. If the preceding tasks have encountered unexpected blocking (which is resolved after a period), check the service logic.

   ```ts
   // HiLog log snippet (simulation), in the following format. The specific value is determined by the application.
   // Log 1: A large number of tasks are submitted.
   // Here taskId is a variable value indicating the task ID, and priority is a variable value indicating the priority. The actual values are subject to the program output.
   taskpool:: Task Allocation: taskId, priority
   taskpool:: Task Allocation: taskId, priority
   taskpool:: Task Allocation: taskId, priority
   taskpool:: Task Allocation: taskId, priority
   taskpool:: Task Allocation: taskId, priority
   ...
   // Log 2: scaling log
   // Here maxNum is a variable value indicating the maximum number of taskpool threads supported, createNum is a variable value indicating the number of taskpool threads currently created, and totalNum is a variable value indicating the total number of taskpool threads currently created. The actual values are subject to the program output. Due to reasons such as log rate limiting optimization in different versions, the logs may be slightly adjusted and may appear as follows:
   Version 1: taskpool:: maxThreads: maxNum, created num: createNum, total num: totalNum
   Version 2: taskpool:: max: maxNum, create: createNum, total: totalNum
   // Log 3: execution state log
   // Here name is a variable value indicating the name of the executed function, taskId is a variable value indicating the task ID, and runningLoopId is a variable value indicating the ID of the loop created by the thread. The actual values are subject to the program output.
   taskpool:: Task Perform: name, taskId, runningLoop: runningLoopId
   ```

3. Check whether exceptions occur during task execution in the TaskPool.

   1. If a JavaScript exception occurs during task execution, the TaskPool catches the JavaScript exception and returns the exception information through **taskpool.execute().catch((e:Error)=>{})**. Review the exception information and rectify the fault.

      <!-- @[catch_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/Index.ets) -->    
      
      ``` TypeScript
      import { taskpool } from '@kit.ArkTS';
      
      @Concurrent
      function createTask(a: number, b: number): number {
        let sum = a + b;
        return sum;
      }
      
      @Entry
      @Component
      struct Index {
        @State message: string | ResourceStr = $r('app.string.Button_label'); // Load the resource. Customize it based on the actual project resources.
      
        build() {
          Row() {
            Column() {
              Text(this.message)
                .fontSize(50)
                .fontWeight(FontWeight.Bold)
                .onClick(() => {
                  console.info(`test start`);
                  // Other business logic
                  // ...
                  let task: taskpool.Task = new taskpool.Task(createTask, 1, 2);
                  taskpool.execute(task).then((res: Object) => {
                    // Process the result after task execution
                    this.message = 'Task execution result: '+ res;
                    // ...
                  }).catch((e: Error) => {
                    // Handle the exception after a task exception occurs
                    // ...
                  })
                })
            }
            .width('100%')
          }
          .height('100%')
        }
      }
      
      // If "test start" is printed in the console but the "Task Allocation: taskId:" log does not appear, taskpool.execute is not executed. The application needs to troubleshoot other business logic.
      ```

   2. If the .catch branch does not return any exception information, but the application's functionality implemented through the tasks is malfunctioning, check whether there are blocking operations in the task logic that cause the function exceptions.

## Troubleshooting for Slow Task Execution in the TaskPool

If there is a significant time gap between the call state log (e.g., **taskpool::add taskId:** or **taskpool::Task Allocation: taskId:**) and the execution state log (**taskpool::Task Perform: name:**), follow this guide for troubleshooting.

### Low-Priority Tasks Delayed by Many Medium-Priority Tasks

**Scenario Example 1**

An application creates a low-priority task that other service scenarios depend on for execution. Subsequently, the application creates many medium-priority tasks, causing the low-priority task to be executed later than planned, and other service scenarios fail to complete tasks at the scheduled time.

**Solution**

Executing tasks with low priority that have timing requirements is not a good choice. Applications should set reasonable task priorities based on service scenarios and properly combine task priorities.

**Scenario Example 2**

The application has a timing requirement for the execution of a certain task (referred to as taskA), with a detection mechanism for execution exceeding 5 seconds. The application sets taskA to medium priority and executes many other tasks with medium priority before taskA, which take 3 to 5 seconds each. These tasks occupy all existing and newly scaled-up threads, causing taskA to exceed 5 seconds from **taskpool.execute** to execution completion.

**Solution**

1. Analyze whether it is reasonable for other tasks to take 3s/5s to execute;
2. Adjust the priority of taskA.

### Tasks in Serial Queue Delayed by Slow Predecessors

**Scenario Example**

If the task is in a serial queue, check the execution of the preceding tasks in that serial queue. As shown in log snippet 1, the serial queue has four tasks, and the problem scenario corresponds to the fourth task. Log snippet 2 reveals that the second task took 2 seconds to execute, which is abnormal for the application's service logic.

```ts
// HiLog log snippet 1 (simulation)
// seqRunner has four tasks.
// Here, 389508780288 is a variable value representing the task ID, and 393913878464 is a variable value representing the seqRunner ID. The actual values depend on the program output.
taskpool:: taskId 389508780288 in seqRunner 393913878464 immediately.
// Here, 394062838784 is a variable value representing the task ID, and 393913878464 is a variable value representing the seqRunner ID. The actual values depend on the program output.
taskpool:: add taskId: 394062838784 to seqRunner 393913878464
// Here, 393918679936 is a variable value representing the task ID, and 393913878464 is a variable value representing the seqRunner ID. The actual values depend on the program output.
taskpool:: add taskId: 393918679936 to seqRunner 393913878464
// Here, 393918673408 is a variable value representing the task ID, and 393913878464 is a variable value representing the seqRunner ID. The actual values depend on the program output.
taskpool:: add taskId: 393918673408 to seqRunner 393913878464

// HiLog log snippet 2 (simulation)
// Check the second task. It takes 2s to complete.
// Here, 394062838784 is a variable value representing the task ID, and 393913878464 is a variable value representing the seqRunner ID. The actual values depend on the program output.
18:28:28.223 taskpool:: taskId 394062838784 in seqRunner 393913878464 immediately.
// Here, name is a variable value representing the executed function name, 394062838784 is a variable value representing the task ID, and 3959344048 is a variable value representing the ID of the loop created by the thread. The actual values depend on the program output.
18:28:28.224 taskpool:: Task Perform: name, 394062838784, runningLoop: 3959344048
// Here, 394062838784 is a variable value representing the task ID, 12 is a variable value representing the date, and 18:28:28.240 is a variable value representing the time. The actual values depend on the program output. Due to reasons such as log rate limiting optimization, logs may be slightly adjusted across different versions, and may appear as follows:
Version 1: 18:28:30.243 taskpool:: Task Perform End: 394062838784
Version 2: 18:28:30.243 taskpool:: Task Perform End: 394062838784, 12 18:28:28.240
```

**Solution**

Further check whether there are time-consuming operations in the service logic of the second task.

### ETS File Containing @Concurrent-Marked Methods Imports Too Many Modules

**Scenario Example**

The first execution of TaskPool tasks is slow, with a delay of several hundred milliseconds. The reason is that before deserialization in the child thread, all modules imported by the .ets file containing @Concurrent-marked methods are initialized, resulting in slow task scheduling. Use trace to further locate the issue. If there are many init module traces before successful deserialization, check whether the .ets file imports too many modules.

**Solution**

1. Split the @Concurrent method into a separate ets file to reduce module initialization time;
2. Use lazy loading ([lazy import](arkts-lazy-import.md)).

## Troubleshooting for TaskPool Serialization Failures

**Symptom**

1. JavaScript exception
   
   Reading the input parameters in serialization fails.

   ```ts
   // Versions earlier than API version 20
   Error message:An exception occurred during serialization, taskpool: failed to serialize arguments.

   // API version 20 and later
   Error message:An exception occurred during serialization, taskpool: failed to serialize arguments.
   Serialize error: Serialize don't support object type: 
   ```

   Failed to deserialize the return value.

   ```ts
   // Versions earlier than API version 20
   Error message:An exception occurred during serialization, taskpool: failed to serialize result.

   // API version 20 and later
   Error message:An exception occurred during serialization, taskpool: failed to serialize result.
   Serialize error: Serialize don't support object type: 
   ```

2. hilog error log

   ```ts
   // Versions earlier than API version 20
   [ecmascript] Unsupported serialize object type: 
   [ecmascript] ValueSerialize: serialize data is incomplete

   // API version 20 and later
   [ecmascript] Serialize don't support object type: 
   [ecmascript] ValueSerialize: serialize data is incomplete
   ```

**Cause**

The input parameters and return results of the function (Concurrent function) that implements a task in TaskPool must meet the object types supported for inter-thread communication. For details, see [serialization support type](../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). When the input parameters or return results of a Concurrent function are of an object type not supported for inter-thread communication, the preceding symptom occurs. The application can further check whether the communication object meets the requirements based on the object type printed in the hilog log.

**Scenario Example**

1. The application throws an exception indicating input parameter serialization failure when starting a task because it passes an unsupported object type for inter-thread communication into the concurrent function.  
**Solution**: The application needs to check the [serialization support type](../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types) to troubleshoot the input parameters of the Concurrent function.

2. When starting a TaskPool task, the application throws an input parameter serialization failure exception, and hilog prints the error log Unsupported serialize object type: Proxy (for API version 20 and later, the error log is: Serialize error: Serialize don't support object type: Proxy). Based on the error log, it can be determined that the application passes a proxy object into the Concurrent function. Troubleshooting the code reveals that the input parameter uses the @State decorator, which causes the original object to actually become a Proxy proxy object. A proxy object is not an object type supported for inter-thread communication.  
**Solution**: TaskPool does not support complex types decorated with @State and @Prop. For details, see [Precautions for TaskPool](taskpool-introduction.md#precautions-for-taskpool). The application should remove the @State decorator.

3. The application throws an exception indicating return value serialization failure when executing a task. The code check shows that the return value of the concurrent function is an unsupported serialization type.

   <!-- @[define_printArgs](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/utils.ets) -->     
   
   ``` TypeScript
   // utils.ets
   @Concurrent
   export function printArgs(args: number) {
     return args;
   }
   ```

   <!-- @[unsupport_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/ExecuteFailedTask.ets) -->     
   
   ``` TypeScript
   // ExecuteFailedTask.ets
   import { taskpool } from '@kit.ArkTS'
   import { BusinessError } from '@kit.BasicServicesKit'
   import { printArgs} from './utils'
   
   @Concurrent
   function createTask(a: number, b: number) {
     let sum = a + b;
     // task1: unsupported serialization type
     let task1: taskpool.Task = new taskpool.Task(printArgs, sum);
     return task1;
   }
   
   function executeTask() {
     // task
     let task: taskpool.Task = new taskpool.Task(createTask, 1, 2);
     taskpool.execute(task).then((res) => {
     }).catch((e: BusinessError) => {
       // Print the exception message "return result serialization failure".
       console.error(`execute task failed ${e.message}`);
     })
   }
   ```

   **Solution**: Create and execute task 1 within **.then**. Set the return value of the concurrent function to a serializable type.

   <!-- @[define_printArgs](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/utils.ets) -->     
   
   ``` TypeScript
   // utils.ets
   @Concurrent
   export function printArgs(args: number) {
     return args;
   }
   ```

   <!-- @[support_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/ExecuteSupportTask.ets) -->     
   
   ``` TypeScript
   // ExecuteSupportTask.ets
   import { taskpool } from '@kit.ArkTS'
   import { BusinessError } from '@kit.BasicServicesKit'
   import { printArgs} from './utils'
   
   @Concurrent
   function createTask(a: number, b: number) {
     // Supported serialization types.
     let sum = a + b;
     return sum;
   }
   
   function executeTask() {
     // task
     let task: taskpool.Task = new taskpool.Task(createTask, 1, 2);
     taskpool.execute(task).then((res) => {
       // task1
       let task1: taskpool.Task = new taskpool.Task(printArgs, res);
     }).catch((e: BusinessError) => {
       console.error(`execute task failed ${e.message}`);
     })
   }
   ```

## Using instanceof with Sendable Objects in Child Threads Returns False

When using the **instanceof** operator in a child thread, the application needs to mark the module exporting Sendable class A in the .ets file with the **use shared** directive to indicate that the module is a [shared module](../arkts-utils/arkts-sendable-module.md).

**Code Example**

<!-- @[test_instanceof](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/TestInstanceof.ets) -->     

``` TypeScript
// pages/TestInstanceof.ets
import { worker, ErrorEvent } from '@kit.ArkTS'
import { A } from './Sendable'

const workerInstance = new worker.ThreadWorker('../workers/Worker.ets');

function testInstanceof() {
  let a = new A();
  if (a instanceof A) {
    // Print "test instanceof in main thread success".
    console.info('test instanceof in main thread success');
  } else {
    console.error('test instanceof in main thread failed');
  }
  workerInstance.postMessageWithSharedSendable(a);
  workerInstance.onerror = (err: ErrorEvent) => {
    console.error('worker err :' + err.message);
  }
}

testInstanceof();
```

<!-- @[define_sendable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/Sendable.ets) -->  

``` TypeScript
// pages/Sendable.ets
'use shared'

@Sendable
export class A {
  public name: string = 'name';

  printName(): string {
    return this.name;
  }
}
```

<!-- @[define_workers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/workers/Worker.ets) -->    

``` TypeScript
// workers/Worker.ets
import { A } from '../pages/Sendable'
import { worker, ThreadWorkerGlobalScope, MessageEvents } from '@kit.ArkTS'

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
workerPort.onmessage = (e: MessageEvents) => {
  let a: A = e.data as A;
  if (a instanceof A) {
    // Print test instanceof in worker thread success.
    console.info(`test instanceof in worker thread success`);
  } else {
    console.error(`test instanceof in worker thread failed`);
  }
}
```

## Troubleshooting for JavaScript Exceptions Thrown by Sendable Features

Due to the fixed layout and the constraint that Sendable objects cannot hold non-Sendable objects, an inappropriate modification to Sendable objects may lead to the throwing of corresponding JavaScript exceptions. Follow this guide for troubleshooting.

### Type Mismatch Exception

**Symptom**

```ts
JavaScript exception: TypeError: Cannot set sendable property with mismatched type
```

**Cause and Solution**

ArkTS runtime strictly checks type consistency during property assignment. If the defined property type does not match the type of the passed object, the above JavaScript exception is thrown. Locate the corresponding service logic based on the JavaScript exception stack.

**Scenario Example**

1. A type mismatch exception is thrown when the application passes an instance of Sendable class A to a child thread. Based on the JavaScript stack, the problem occurs when creating an instance of class A. It is found that when the application is integrated with other modules, the other modules do not use Sendable class B to encapsulate the dataset.   
**Solution**: Use a Sendable class to re-encapsulate the data passed by other modules into the current module.

   <!-- @[define_resolveOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/SolveMismatchTypeOne.ets) -->    
   
   ``` TypeScript
   @Sendable
   export class B {
     constructor() {}
   }
   
   @Sendable
   export class A {
     constructor(b: B) {
       this.b = b;
     }
   
     public b: B | undefined = undefined;
   }
   ```

2. A type mismatch exception is thrown when the application runs the assignment statement **this.g = g**. It is found that the property **g** uses the @State decorator, causing the original object to become a Proxy object, resulting in a type mismatch.  
**Solution**: Remove the @State decorator.

3. A custom Sendable class inherits from collections.Array and overrides the constructor. When the slice function is called after the class is instantiated, a type mismatch exception will be thrown. This is because when the slice function is called, collections.Array creates a new SendableArray internally. The input parameter of the constructor is the length of the new array, which is of number type. Since **ans** is of the string type, and the input parameter of the number type is used to assign a value to **ans** in the constructor, assigning a value of number type to a variable of string type is not allowed in the Sendable class. As a result, an exception is thrown.

   <!-- @[define_resolveTwo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/SolveMismatchTypeTwo.ets) -->     
   
   ``` TypeScript
   // pages/SolveMismatchTypeTwo.ets
   import { collections } from '@kit.ArkTS'
   
   @Sendable
   export class CollectionsArray extends collections.Array<string> {
     public ans: string = 'test';
     constructor(heldValue: string) {
       super();
       this.ans = heldValue;
     }
   }
   let arr = new CollectionsArray('test');
   arr.slice(1);
   ```

   **Solution**: Use an independent API to assign values to properties.

   <!-- @[define_resolveThree](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/SolveMismatchTypeThree.ets) -->    
   
   ``` TypeScript
   // pages/SolveMismatchTypeThree.ets
   import { collections } from '@kit.ArkTS'
   
   @Sendable
   export class CollectionsArray extends collections.Array<string> {
     public ans: string = 'test';
   
     constructor() {
       super();
     }
   
     set(str: string) {
       this.ans = str;
     }
   }
   
   let arr = new CollectionsArray();
   arr.slice(1);
   arr.set('success');
   ```

### Adding Property Exception

**Symptom**

```ts
JavaScript exception: TypeError: Cannot add property in prevent extensions
```

**Cause and Solution**

Since the layout of Sendable classes is fixed and does not allow adding or removing properties, adding a new property to a Sendable object will throw the above JavaScript exception. Locate the corresponding .ts file code line based on the JavaScript exception stack and check the relevant service logic.

**Scenario Example**

1. The application defines a Sendable class and a namespace with the same name in the same .ets file. An exception is thrown when the application attempts to add a new property. Since TS merges classes and namespaces with the same name, appending the exports of the namespace to the class with the same name effectively adds a new property to the Sendable class, causing the exception.  
**Solution**: Due to specification limitations, merging Sendable classes and namespaces with the same name is currently not supported.

2. An exception is thrown when the application attempts to add a new property while using the Sendable feature in a HAR. The exception code line is located in a .js file, and the Sendable feature is not supported in .js files, resulting in the exception.  
**Solution**: When using the Sendable feature in the HAR, [configure UseTsHar](sendable-constraints.md#rules-for-using-sendable-in-hars).

3. An exception is thrown when the application attempts to add a new property while using the Sendable feature in Local Test or Previewer. Since the Sendable feature is currently not supported in Local Test and Previewer, the exception is thrown.  
**Solution**: Due to specification limitations, this is currently not supported.

## What Is the Principle Behind ArkTS Promise?

Promise is the asynchronous concurrency capability provided by ArkTS and is a standard JavaScript syntax. For details, see [Promise](async-concurrency-overview.md#promise).

## Can TaskPool Threads Execute JavaScript Closure Functions That Do Not Require @Concurrent and @Sendable Decorators?

Task functions executed by the TaskPool must be decorated with @Concurrent. Since concurrent functions cannot access closures, they cannot call other regular functions within the same file. For details, see [Precautions for TaskPool](taskpool-introduction.md#precautions-for-taskpool). However, you can pass @Sendable-decorated regular functions and async functions as parameters to concurrent functions and call Sendable functions within the concurrent functions.

TaskPool threads do not support executing regular JavaScript closure functions. If necessary, you can use the [Worker](worker-introduction.md) concurrency capability to reconstruct your services.

## What Are the Similarities and Differences Between @Concurrent Decorated Functions and async Functions?

1. Concurrent functions are usually used together with TaskPool to complete asynchronous concurrent tasks. async is a Promise syntax sugar for handling asynchronous operations. An async function returns a Promise object to implement asynchronous operations. The `constructor.name` property of both types of functions is `'AsyncFunction'`, and the result of the async function type check through [isAsyncFunction](../reference/apis-arkts/js-apis-util.md#isasyncfunction8) is true for both.
2. An async function automatically wraps the return value into a Promise. The return value of a Concurrent function remains consistent with that of the decorated function and is not automatically wrapped.
3. A Concurrent function cannot access closures, and cannot call other regular functions in the current file. An async function has no such restriction.
4. When [errorManager](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md) is used for exception capture, the @Concurrent decorator does not change the exception capture behavior of the decorated function. An async function is captured by [globalUnhandledRejectionDetected](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md#errormanageronglobalunhandledrejectiondetected18) and [unhandledRejection](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md#errormanageronunhandledrejection12).

## How Do I Save the Execution Result of a TaskPool Task to a Custom Data Structure?

**Symptom**

The execution function (concurrent function) of a TaskPool task can only use local variables and function parameters. How should I save its execution result of a TaskPool task to a custom data structure?

**Solution**

1. Custom Sendable class: [Sendable objects](arkts-sendable.md) can be shared across different threads. You can save the task execution results within these objects.

2. Returning results in **.then**: The execution result of a TaskPool task can be returned within **.then**. If the data to be saved is only used in the current thread, the execution result can be stored in a custom data structure within **.then**.

   <!-- @[define_sendableTwo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/Sendable.ets) -->      
   
   ``` TypeScript
   // Sendable.ets, located in the same directory as Index.ets.
   @Sendable
   export class TestClass {
     public name: string = 'test';
   
     setName(name: string) {
       this.name = name;
     }
   
     getName(): string {
       return this.name;
     }
   }
   ```

   <!-- @[save_result](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/SaveResult.ets) -->      
   
   ``` TypeScript
   // SaveResult.ets
   import { taskpool } from '@kit.ArkTS'
   import { BusinessError } from '@kit.BasicServicesKit'
   import { TestClass } from './Sendable'
   
   @Concurrent
   function createTask(a: number): string {
     return `test${a}`;
   }
   
   function executeTask() {
     let testObject: TestClass = new TestClass();
     let task: taskpool.Task = new taskpool.Task(createTask, 1)
     taskpool.execute(task).then((res) => {
       testObject.setName(res as string);
       console.info(`execute task success, name is ${testObject.getName()}`);
     }).catch((e: BusinessError) => {
       console.error(`execute task error: ${e.message}`);
     })
   }
   ```

## Sendable Class Cannot Be Loaded in a Child Thread

**Symptom**

The class decorated with **Sendable** and the class decorated with **Observed** are defined in the same .ets file. When the TaskPool child thread loads the Sendable class, the error message "SendableItem is not initialized" is displayed.

<!-- @[initialize_item](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/SolveItemInitialized.ets) -->     

``` TypeScript
// pages/SolveItemInitialized.ets
import { taskpool } from '@kit.ArkTS'
import { BusinessError } from '@kit.BasicServicesKit'
import { SendableItem } from './Sendable'

@Concurrent
function createTask() {
  let data = new SendableItem();
}

function executeTask() {
  let task = new taskpool.Task(createTask);
  taskpool.execute(task).then((res) => {
    console.info(`execute task success`);
  }).catch((e: BusinessError) => {
    console.error(`execute task error: ${e.message}`);
  })
}

executeTask();
```

```ts
// sendable.ets
@Observed
export class NormalItem {
  age: number = 0;
}

@Sendable
export class SendableItem {
  name: string = '';
}
```

**Root Cause**

The Observed decorator can be used only in the UI thread. It cannot be directly or indirectly used in the child thread, Worker, or TaskPool. Otherwise, application malfunctions or even crashes may occur. Since the **sendable.ets** file defines a class decorated with the Observed decorator, this class may still be parsed and executed even if it is not explicitly invoked. When the parser encounters a UI decorator such as Observed, it will throw an exception: "Observed is not defined", which interrupts the parsing of other modules in the current file. The exception "SendableItem is not initialized" is thrown when the TaskPool child thread loads the Sendable class.

**Solution**

After the NormalItem class decorated with Observed is separated to a separate .ets file, and the TaskPool child thread loads the Sendable class SendableItem, the application runs as expected.

<!-- @[initialize_item](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/SolveItemInitialized.ets) -->     

``` TypeScript
// pages/SolveItemInitialized.ets
import { taskpool } from '@kit.ArkTS'
import { BusinessError } from '@kit.BasicServicesKit'
import { SendableItem } from './Sendable'

@Concurrent
function createTask() {
  let data = new SendableItem();
}

function executeTask() {
  let task = new taskpool.Task(createTask);
  taskpool.execute(task).then((res) => {
    console.info(`execute task success`);
  }).catch((e: BusinessError) => {
    console.error(`execute task error: ${e.message}`);
  })
}

executeTask();
```

<!-- @[define_sendableThree](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/Sendable.ets) -->

``` TypeScript
// Sendable.ets
@Sendable
export class SendableItem {
  public name: string = '';
}
```

<!-- @[define_normalItem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrencyFaq/entry/src/main/ets/pages/ui.ets) -->

``` TypeScript
// ui.ets
@Observed
export class NormalItem {
  public age: number = 0;
}
```
