---
kits: ["ArkTS / Ark programming language"]
description: "Provides multi-threaded development guidance for synchronous tasks: for synchronous tasks that may block the UI main thread, this document demonstrates two approaches—using TaskPool to process synchronous tasks and using Worker to process interrelated synchronous tasks—to prevent synchronous calls from causing application lag."
keywords: [synchronous task, TaskPool, Worker, main thread blocking, application lag, interrelated tasks, multi-threaded processing]
doctype: guide
status: active
---

# Synchronous Task Development (TaskPool and Worker)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:47:37.229Z pushedAt=2026-11-12T13:32:21.559Z nl=1 -->


Synchronous tasks ensure that tasks are executed in a specific order and according to specific rules through collaboration and synchronization among multiple threads (for example, using locks to prevent data races), thereby guaranteeing data correctness and correct program execution.

TaskPool is well-suited for independent synchronous tasks. Therefore, it is recommended for scenarios where synchronous tasks are relatively independent, such as a series of static methods or methods implemented using a singleton pattern. Conversely, if synchronous tasks are interdependent, Worker is the better choice.


## Using TaskPool for Independent Synchronous Tasks

TaskPool is recommended in the following scenarios:

- Tasks that are scheduled independently.
                        
- Tasks that are implemented using static methods.

- Singleton handles or class objects used across threads.

> **NOTE**
>
> Due to the memory isolation between threads in the [Actor model](multi-thread-concurrency-overview.md#actor-model), non-thread-safe singletons cannot be used across threads. This issue can be resolved by exporting the singleton through a shared module.

1. Define a concurrent function to implement service logic.

2. Create a [task](../reference/apis-arkts/js-apis-taskpool.md#task), and execute the task using the [execute()](../reference/apis-arkts/js-apis-taskpool.md#taskpoolexecute-1) interface.

3. Perform operations on the task result.

In the following example, the service logic uses TaskPool to call related synchronous methods. First, define the concurrent function **taskpoolFunc**, which must be decorated with [@Concurrent](taskpool-introduction.md#concurrent-decorator). Then, define the function **mainFunc**, which creates tasks, executes them, and processes the results returned by the tasks.

<!-- @[taskpool_handle_sync_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/SyncTaskDevelopment.ets) --> 

``` TypeScript
import { taskpool } from '@kit.ArkTS';
// ...

// Step 1: Define the concurrent function to implement the business logic.
@Concurrent
async function taskpoolFunc(num: number): Promise<number> {
  // Implement the corresponding functionality based on the business logic.
  let tmpNum: number = num + 100;
  return tmpNum;
}

async function mainFunc(): Promise<void> {
  // Step 2: Create and execute the task.
  let task1: taskpool.Task = new taskpool.Task(taskpoolFunc, 1);
  let res1: number = await taskpool.execute(task1) as number;
  let task2: taskpool.Task = new taskpool.Task(taskpoolFunc, res1);
  let res2: number = await taskpool.execute(task2) as number;
  // Step 3: Operate on the result returned by the task.
  console.info(`taskpool: task res1 is: ${res1}`);
  console.info(`taskpool: task res2 is: ${res2}`);
}

const MSG_SET = 0;
const MSG_GET = 1;

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
          .onClick(async () => {
            await mainFunc();
            // ...
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```


## Using Worker for Interdependent Synchronous Tasks

When a series of synchronous tasks needs to be scheduled using the same handle, or when they depend on a specific class object that cannot be shared across different task pools, Worker is the appropriate choice.

1. Create a Worker object in the UI main thread and receive messages from the Worker thread. DevEco Studio supports generation of Worker templates with a single click. In the corresponding {moduleName} directory, right-click anywhere and choose **New** > **Worker** to automatically generate the Worker template files and configuration information.

    <!-- @[worker_handle_associated_sync_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/SyncTaskDevelopment.ets) --> 
    
    ``` TypeScript
    import { MessageEvents, worker } from '@kit.ArkTS';
    // ...
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
              .onClick(async () => {
                // ...
                let w: worker.ThreadWorker = new worker.ThreadWorker('entry/ets/workers/MyWorker2.ets');
                w.onmessage = (e: MessageEvents): void => {
                  // Receive the result from the Worker subthread.
                  console.info(`main thread onmessage, ${e.data.message}`);
                  // Destroy the Worker.
                  if (e.data.isTerminate) {
                    w.terminate();
                  }
                }
                // Send a Set message to the Worker subthread.
                w.postMessage({'type': MSG_SET, 'data': 10});
                // Send a Get message to the Worker subthread.
                w.postMessage({'type': MSG_GET});
              })
          }
          .width('100%')
        }
        .height('100%')
      }
    }
    ```


2. Bind the Worker object in the Worker thread and process the synchronous task logic.

    <!-- @[worker_handle_associated_sync_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/workers/handle.ts) -->  
    
    ``` TypeScript
    export default class Handle {
      id: number = 0;
    
      syncGet(): number {
        return this.id;
      }
    
      syncSet(num: number): boolean {
        this.id = num;
        return true;
      }
    }
    ```

    <!-- @[worker_handle_associated_sync_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/workers/MyWorker2.ets) --> 
    
    ``` TypeScript
    import { worker, ThreadWorkerGlobalScope, MessageEvents } from '@kit.ArkTS';
    // Import the handle type.
    import Handle from './handle'; 
    
    const MSG_SET = 0;
    const MSG_GET = 1;
    
    let workerPort : ThreadWorkerGlobalScope = worker.workerPort;
    
    // Handle that cannot be transferred. All operations depend on this handle.
    let handler: Handle = new Handle();
    
    // onmessage() logic of the Worker thread.
    workerPort.onmessage = (e : MessageEvents): void => {
      switch (e.data.type as number) {
        case MSG_SET:
          let result: boolean = handler.syncSet(e.data.data);
          console.info('worker: result is ' + result);
          workerPort.postMessage({'message': 'the result of syncSet() is ' + result, 'isTerminate': false});
          break;
        case MSG_GET:
          let num: number = handler.syncGet();
          console.info('worker: num is ' + num);
          workerPort.postMessage({'message': 'the result of syncGet() is ' + num, 'isTerminate': true});
          break;
        default:
          workerPort.postMessage({ 'message': 'send message is invalid', 'isTerminate': false });
          break;
      }
    }
    ```
