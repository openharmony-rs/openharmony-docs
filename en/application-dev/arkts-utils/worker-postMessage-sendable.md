# High-Performance Communication Between Multi-Level Workers
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=354aaf2b88462afa3a548efc47aadf9e83e04919 translatedAt=2026-11-04T09:41:51.381Z pushedAt=2026-11-04T09:43:06.156Z nl=1 -->

It is a common requirement for communication between multi-level [Workers](worker-introduction.md) (where child Workers are created by parent Workers, forming a hierarchy). Since you are responsible for managing the lifecycles of Worker threads, it is crucial to properly manage the lifecycles of multi-level Workers. You should ensure that all child Workers are destroyed before the parent Worker is destroyed.

This document describes how to implement high-performance message communication between multi-level Workers. The key to high-performance message communication lies in [Sendable objects](arkts-sendable.md). Combined with [postMessageWithSharedSendable](../reference/apis-arkts/js-apis-worker.md#postmessagewithsharedsendable12), you can achieve high-performance object transfer between threads. For example, in a data cloning scenario, assume there is one parent Worker and two child Workers. The parent Worker is responsible for creating child Workers and sending data cloning tasks to them. The child Workers receive the tasks, perform data cloning operations, and return the cloning results to the parent Worker upon completion.

1. Create the **Sendable** folder in the **ets** folder, and prepare the Sendable class **CopyEntry** to encapsulate cloning task data.

   <!-- @[copy_entry_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/Sendable/CopyEntry.ets) -->     
   
   ``` TypeScript
   // CopyEntry.ets
   @Sendable
   export class CopyEntry {
     // Clone type.
     type: string;
     // File path.
     filePath: string;
     constructor(type: string, filePath: string) {
       this.type = type;
       this.filePath = filePath;
     }
   }
   ```

2. Create two Worker files. DevEco Studio supports generating a Worker with one click. Right-click anywhere in the corresponding {moduleName} directory and choose New &gt; Worker to automatically generate the Worker template file and configuration information. This document uses creating "ParentWorker" (parent Worker) and "ChildWorker" (child Worker) as an example. The parent Worker is responsible for distributing cloning tasks, and the child Worker is responsible for receiving tasks, performing data cloning operations, and notifying the parent Worker after the task is complete. After receiving the task completion message from a child Worker, the parent Worker destroys and closes that child Worker. After all child Worker tasks are complete and all child Workers are destroyed and closed, the parent Worker destroys and closes itself.
  
   <!-- @[parent_worker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/workers/ParentWorker.ets) -->       
   
   ``` TypeScript
   // ParentWorker.ets
   import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker, collections, ArkTSUtils } from '@kit.ArkTS';
   import { CopyEntry } from '../Sendable/CopyEntry';
   
   const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
   
   // Calculate the number of tasks of worker1.
   let count1 = 0;
   // Calculate the number of tasks of worker2.
   let count2 = 0;
   // Calculate the total number of tasks.
   let sum = 0;
   // Asynchronous lock.
   const asyncLock = new ArkTSUtils.locks.AsyncLock();
   // Create a child Worker.
   const copyWorker1 = new worker.ThreadWorker('entry/ets/workers/ChildWorker.ets');
   const copyWorker2 = new worker.ThreadWorker('entry/ets/workers/ChildWorker.ets');
   
   workerPort.onmessage = (e: MessageEvents) => {
     let array = e.data as collections.Array<CopyEntry>;
     sum = array.length;
     for (let i = 0; i < array.length; i++) {
       let entry = array[i];
       if (entry.type === 'copy1') {
         count1++;
         // If the data type is copy1, transfer the data to copyWorker1.
         copyWorker1.postMessageWithSharedSendable(entry);
       } else if (entry.type === 'copy2') {
         count2++;
         // If the data type is copy2, transfer the data to copyWorker2.
         copyWorker2.postMessageWithSharedSendable(entry);
       }
     }
   };
   
   copyWorker1.onmessage = async (e: MessageEvents) => {
     console.info('copyWorker1 onmessage:' + e.data);
     await asyncLock.lockAsync(() => {
       count1--;
       if (count1 === 0) {
         // If all tasks of copyWorker1 are complete, close copyWorker1.
         console.info('copyWorker1 close');
         copyWorker1.terminate();
       }
       sum--;
       if (sum === 0) {
         // If all tasks are complete, close the parent Worker.
         workerPort.close();
       }
     });
   }
   
   copyWorker2.onmessage = async (e: MessageEvents) => {
     console.info('copyWorker2 onmessage:' + e.data);
     await asyncLock.lockAsync(() => {
       count2--;
       sum--;
       if (count2 === 0) {
         // If all tasks of copyWorker2 are complete, close copyWorker2.
         console.info('copyWorker2 close');
         copyWorker2.terminate();
       }
       if (sum === 0) {
         // If all tasks are complete, close the parent Worker.
         workerPort.close();
       }
     });
   }
   
   workerPort.onmessageerror = (e: MessageEvents) => {
     console.error('onmessageerror:' + e.data);
   }
   
   workerPort.onerror = (e: ErrorEvent) => {
     console.error('onerror:' + e.message);
   }
   ```
   
   <!-- @[child_worker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/workers/ChildWorker.ets) -->     
   
   ``` TypeScript
   // ChildWorker.ets
   import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
   import { CopyEntry } from '../Sendable/CopyEntry';
   
   const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
   
   workerPort.onmessage = (e: MessageEvents) => {
     let data = e.data as CopyEntry;
     // The copy operation is omitted.
     console.info(data.filePath);
     workerPort.postMessageWithSharedSendable('done');
   };
   
   workerPort.onmessageerror = (e: MessageEvents) => {
     console.error('onmessageerror:' + e.data);
   };
   
   workerPort.onerror = (e: ErrorEvent) => {
     console.error('onerror:' + e.message);
   };
   ```

3. On the main thread page of the UI, create a parent Worker, prepare the data required for the cloning task, and send the data to the parent Worker.

   <!-- @[multi_worker_high_performance_communication](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/WorkerPostMessageSendable.ets) -->   
   
   ``` TypeScript
   // Index.ets
   import { worker, collections } from '@kit.ArkTS';
   import { CopyEntry } from '../Sendable/CopyEntry';
   
   function promiseCase() {
     let p: Promise<void> = new Promise<void>((resolve: Function, reject: Function) => {
       setTimeout(() => {
         resolve();
       }, 100);
     });
     return p;
   }
   
   async function postMessageTest() {
     let ss = new worker.ThreadWorker('entry/ets/workers/ParentWorker.ets');
     let isTerminate = false;
     ss.onexit = () => {
       isTerminate = true;
     };
     let array = new collections.Array<CopyEntry>();
     // Prepare data.
     for (let i = 0; i < 4; i++) {
       if (i % 2 == 0) {
         array.push(new CopyEntry('copy1', 'file://copy1.txt'));
       } else {
         array.push(new CopyEntry('copy2', 'file://copy2.txt'));
       }
     }
     // Send a message to the Worker thread.
     ss.postMessageWithSharedSendable(array);
     while (!isTerminate) {
       await promiseCase();
     }
     console.info('Worker thread has exited');
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
               postMessageTest();
               // ...
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
