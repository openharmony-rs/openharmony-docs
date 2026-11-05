# Real-Time Communication Between the Worker Thread and Host Thread
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=90bafeeb8be1710ba45283072539a7fe269de2b1 translatedAt=2026-11-04T09:41:13.176Z pushedAt=2026-11-04T09:42:58.189Z nl=1 -->


In ArkTS, Worker differs from TaskPool to a certain extent: it has a quantity limit but can exist for a long time. A [Worker](worker-introduction.md) may execute multiple different tasks, and the execution duration or return result of each task may differ. The host thread needs to call different methods in the Worker as appropriate, while the Worker needs to return results to the host thread in a timely manner.


The following example demonstrates how a Worker can respond to a "hello world" request.


1. First, create a Worker that executes tasks. For details about how to create it, see [Precautions for Creating a Worker](worker-introduction.md#precautions-for-creating-a-worker).

   <!-- @[create_worker_execute_multi_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/workers/Worker.ets) --> 
   
   ``` TypeScript
   import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
   
   const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
   
   workerPort.onmessage = (e: MessageEvents) => {
     // ...
     if (e.data === 'hello world') {
       workerPort.postMessage('success');
     }
   }
   ```

2. The host thread here is the UI main thread. Create a Worker object in the host thread. When "Hello World" is clicked, call the postMessage method to send a message to the Worker thread. The Worker thread processes the message sent by the host thread through the registered onmessage callback.

   <!-- @[respond_worker_instant_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/WorkerCommunicatesWithMainthread.ets) -->
   
   ``` TypeScript
   import { worker, ErrorEvent, MessageEvents } from '@kit.ArkTS';
   
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
               // Create a Worker thread instance.
               const ss: worker.ThreadWorker = new worker.ThreadWorker('entry/ets/workers/Worker.ets');
   
               // Receive the message sent by the Worker thread, refresh the success state upon receipt, and destroy the Worker.
               ss.onmessage = (e: MessageEvents): void => {
                 console.info('worker:: res is ' + e.data);
                 this.message = 'success';
                 // Destroy the Worker thread in the callback to avoid resource leakage.
                 ss.terminate();
               };
   
               // Capture global exceptions during the Worker thread lifecycle and refresh the failure state (API version 18+).
               ss.onAllErrors = (err: ErrorEvent): void => {
                 console.error('worker:: error is ' + err.message);
                 this.message = 'failed';
               };
   
               // Send a message to the Worker thread.
               ss.postMessage('hello world');
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

In the sample code, the Worker receives the message from the host thread, processes it, and returns the result to the host thread. This implements instant communication between the host thread and the Worker, allowing the host thread to conveniently use the Worker's execution results.
