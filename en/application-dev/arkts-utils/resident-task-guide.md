# Resident Task Development Guide (Worker)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-11-04T09:28:19.905Z pushedAt=2026-11-04T09:37:06.205Z nl=1 -->

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
         // Start the resident task.
         performTask();
       }
     } else if (type === 'stop') {
       isRunning = false;
     }
   }
   
   // Simulate the resident task.
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
