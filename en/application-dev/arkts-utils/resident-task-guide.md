---
kits: ["ArkTS / Ark programming language"]
description: "Provides guidance on using Worker to develop resident tasks: a Worker continuously executes tasks until the host thread sends a termination command. The example demonstrates automatic Worker creation, start and stop command interaction, and task execution, suitable for services that require long-term background running. It also provides guidance on Worker quantity planning and reuse."
keywords: [resident task, Worker, ThreadWorker, resident thread, start and stop commands, background running, lifecycle management, Worker reuse, Worker quantity planning]
doctype: guide
status: active
---

# Resident Task Development Guide (Worker)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=3621e01243307de1ff4f06e11dd17a074cf484af translatedAt=2026-11-06T10:41:52.192Z pushedAt=2026-11-12T09:09:39.673Z nl=1 -->

This topic describes how to use Worker to execute a resident task. Worker continuously executes the task until it receives a termination command from the host thread.

The development process and example are outlined as follows:

1. Create Worker with DevEco Studio. Specifically, in DevEco Studio, right-click anywhere in the {moduleName} directory and choose **New > Worker** to automatically generate the Worker template file and configuration information. In this example, we will create a Worker named "Worker".

   You can also manually create Worker thread files. For specific methods and related considerations, see [Precautions for Creating a Worker](worker-introduction.md#precautions-for-creating-a-worker).

2. Import the Worker module, and then call [constructor()](../reference/apis-arkts/js-apis-worker.md#constructor9) of ThreadWorker in the host thread to create a Worker object. The thread that creates the Worker object is the host thread. Enable the host thread to send messages. The host thread (UI main thread) sends 'start' to initiate a long-running task and receive messages from the Worker thread. When the task is no longer needed, the host thread sends 'stop' to terminate the task. In this example, the task is terminated after 10 seconds.

   <!-- @[worker_receive_child_thread_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/ResidentTaskGuide.ets) --> 
   
   ``` TypeScript
   import { MessageEvents, worker } from '@kit.ArkTS';
   
   @Entry
   @Component
   struct Index {
     build() {
       Column() {
         Text('Listener task')
           .id('HelloWorld')
           .fontSize(50)
           .fontWeight(FontWeight.Bold)
           .onClick(() => {
             const workerInstance: worker.ThreadWorker = new worker.ThreadWorker('entry/ets/workers/Worker.ets');
             workerInstance.onmessage = (event: MessageEvents) => {
               console.info('UI main thread received message: ', event.data);
             }
             workerInstance.postMessage({type: 'start'})
             // Stop the worker after 10 seconds.
             setTimeout(() => {
               workerInstance.postMessage({ type: 'stop' });
             }, 10000);
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```

3. Handle messages in the Worker thread. When receiving 'start' from the host thread, the Worker thread starts executing the long-running, non-periodic task and sends messages back to the host thread in real-time. When receiving 'stop', it terminates the task and sends a corresponding message back to the host thread.

   <!-- @[worker_correspond_main_thread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/workers/Worker.ets) -->
   
   ``` TypeScript
   import { MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
   
   const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
   let isRunning = false;
   workerPort.onmessage = (e: MessageEvents) => {
     const type = e.data.type as string;
     if (type === 'start') {
       if (!isRunning) {
         isRunning = true;
         // Start a resident task.
         performTask();
       }
     } else if (type === 'stop') {
       isRunning = false;
     }
   }
   
   // Simulate a resident task.
   function performTask() {
     if (isRunning) {
       // Simulate a long-running task.
       workerPort.postMessage('Worker is performing a task');
       // Execute the task again after 1 second.
       setTimeout(performTask, 1000);
     } else {
       workerPort.postMessage('Worker has stopped performing the task');
       workerPort.close();
     }
   }
   ```

## Worker Quantity Planning and Reuse

For scenarios that require multiple resident Workers, more Workers is not always better. When each Worker is created, it initializes an independent VM instance, independent heap memory, interpreter, and module system, with a base memory overhead of approximately several MB to 20 MB (for details on the memory overhead composition, see [Worker Operation Mechanism](worker-introduction.md#worker-operating-mechanism)). Too many Workers can cause significant memory pressure on low-memory devices. Therefore, the number of Workers should be determined by the number of tasks that need to run in parallel at the same time, and a small number of Workers should be used to handle multiple types of tasks whenever possible.

The steps for planning the number of Workers are as follows:

1. List all resident tasks and mark which tasks need to run in parallel at the same time.

2. Merge tasks that can be reused serially into a single Worker and dispatch them through the type field in the message.

3. The final number of Workers equals the number of parallel task groups that cannot be further divided after merging.

For example, if an application has 3 resident tasks (data parsing, log reporting, and file preprocessing), where log reporting and file preprocessing can serially reuse the same Worker while data parsing needs to run independently in parallel, then only 2 Workers are ultimately required.

For multiple types of tasks merged into the same Worker, the host thread can encapsulate a task management class to distinguish task types through the type field in the message and dispatch them accordingly. An example is as follows:

<!-- @[worker_manager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/WorkerManager.ets) -->

``` TypeScript
import { worker, MessageEvents } from '@kit.ArkTS';

// Message sent from the host thread to the worker. Distinguish task types by the type field.
interface WorkerMessage {
  id: number;
  type: string;
  payload: string;
}

// Processing result returned by the worker to the host thread.
interface WorkerResult {
  id: number;
  success: boolean;
  result?: string;
  error?: string;
}

class WorkerManager {
  private workerInstance: worker.ThreadWorker | null = null;
  private taskCounter: number = 0;
  private pending: Map<number, (result: string) => void> = new Map();
  private rejectFuncs: Map<number, (reason: string) => void> = new Map();

  constructor() {
    this.workerInstance = new worker.ThreadWorker('entry/ets/workers/Dispatcher.ets');
    this.workerInstance.onmessage = (e: MessageEvents) => {
      const data = e.data as WorkerResult;
      if (data.success) {
        const resolver = this.pending.get(data.id);
        if (resolver) {
          resolver(data.result ?? '');
          this.pending.delete(data.id);
          this.rejectFuncs.delete(data.id);
        }
      } else {
        const reject = this.rejectFuncs.get(data.id);
        if (reject) {
          reject(data.error ?? '');
          this.pending.delete(data.id);
          this.rejectFuncs.delete(data.id);
        }
      }
    };

    this.workerInstance.onexit = (code) => {
      this.pending.clear();
      this.rejectFuncs.forEach(reject => reject('Worker exited'));
      this.rejectFuncs.clear();
    };
  }

  // Reuse the same worker for different types of tasks. Dispatch by type.
  execute(type: string, payload: string): Promise<string> {
    const id = ++this.taskCounter;
    return new Promise<string>((resolve, reject) => {
      if (this.workerInstance) {
        this.pending.set(id, resolve);
        this.rejectFuncs.set(id, reject);
        const message: WorkerMessage = { id, type, payload };
        this.workerInstance.postMessage(message);
      } else {
        reject('Worker is null');
      }
    });
  }

  destroy(): void {
    if (this.workerInstance) {
      this.workerInstance.terminate();
      this.workerInstance = null;
    }
  }
}

// Global singleton. Reuse a single worker through this management class to process multiple serializable task types (tasks requiring independent parallelism should be handled by separate workers).
const dispatcher: WorkerManager = new WorkerManager();

async function executeDemo() {
  try {
    let result = await dispatcher.execute('logReport', 'payload');
    console.info(`Execute result: ${result}`);
  } catch (e) {
    console.error(`Execute error: ${e}`);
  }
}
executeDemo();
```

<!-- @[worker_dispatcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/workers/Dispatcher.ets) -->

``` TypeScript
// workers/Dispatcher.ets
import { MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

interface WorkerMessage {
  id: number;
  type: string;
  payload: string;
}

interface WorkerResult {
  id: number;
  success: boolean;
  result?: string;
  error?: string;
}

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (e: MessageEvents) => {
  const data = e.data as WorkerMessage;
  try {
    let result: string = '';
    // Dispatch messages to the corresponding processing logic based on the type field. Reuse the same worker serially for multiple task types.
    if (data.type === 'logReport') {
      result = logReport(data.payload);
    } else if (data.type === 'filePreprocess') {
      result = filePreprocess(data.payload);
    }
    const message: WorkerResult = { id: data.id, success: true, result: result };
    workerPort.postMessage(message);
  } catch (error) {
    const message: WorkerResult = { id: data.id, success: false, error: error.message };
    workerPort.postMessage(message);
  }
};

function logReport(payload: string): string {
  // Log reporting logic.
  return 'logReport done';
}

function filePreprocess(payload: string): string {
  // File preprocessing logic.
  return 'filePreprocess done';
}
```
