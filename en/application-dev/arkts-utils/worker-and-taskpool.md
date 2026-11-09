# Persistent Worker Threads Handling Concurrent Tasks via TaskPool
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=5f2bc820d02c0fb06b1bd1ea2345bc0bf048c408 translatedAt=2026-11-04T09:40:56.539Z pushedAt=2026-11-04T09:42:49.757Z nl=1 -->

In ArkTS application development, you can choose between TaskPool and Worker threads for concurrent task processing, or you utilize both capabilities.

This section describes how to execute concurrent tasks through TaskPool within a Worker thread.

1. Create a Worker thread in the main thread and send a message.

   <!-- @[worker_taskpool](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/pages/workerAndTaskpool.ets) -->
   
   ``` TypeScript
   // workerAndTaskpool.ets
   import { MessageEvents, worker } from '@kit.ArkTS';
   import { PromptAction } from '@kit.ArkUI';
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'Create a Worker thread in the main thread and send a message.';
     @State returnMessage: string = 'return...';
     @State promptAction: PromptAction = this.getUIContext().getPromptAction();
   
     build() {
       RelativeContainer() {
         Button(this.message)
           .fontSize(19)
           .id('HelloWorld')
           .fontWeight(FontWeight.Bold)
           .alignRules({
             center: { anchor: '__container__', align: VerticalAlign.Center },
             middle: { anchor: '__container__', align: HorizontalAlign.Center }
           })
           .onClick(() => {
             // 1. Create a Worker instance.
             const myWorker = new worker.ThreadWorker('entry/ets/workers/Worker.ets');
   
             // 2. Register the onmessage callback to handle messages sent from the Worker to the main thread.
             myWorker.onmessage = (e: MessageEvents) => {
               console.info('Main thread receives the final result:', e.data.result);
               this.returnMessage = 'Main thread receives the final result:' + e.data.result;
               this.promptAction.showToast({ message: this.returnMessage });
               myWorker.terminate(); // Terminate the Worker at an appropriate time.
             };
   
             // 3. Send a startup command to the Worker.
             myWorker.postMessage({ type: 'start', data: 10 });
           })
         // ...
       }
       .height('100%')
       .width('100%')
     }
   }
   ```

2. Call TaskPool to execute concurrent tasks in the Worker thread.

   <!-- @[define_worker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/workers/Worker.ets) -->
   
   ``` TypeScript
   // Worker.ets
   import { MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
   import { taskpool } from '@kit.ArkTS';
   
   const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
   workerPort.onmessage = async (e: MessageEvents) => {
     if (e.data.type === 'start') {
       // Simulate Worker data processing.
       const processedData = heavyComputation(e.data.data);
   
       // Call TaskPool to execute concurrent tasks.
       const task = new taskpool.Task(parallelTask, processedData);
       const result = await taskpool.execute(task);
       console.info('TaskPool thread returned result: ', result);
   
       // Return the final result to the main thread.
       workerPort.postMessage({
         status: 'success',
         result: result
       });
     }
   }
   
   function heavyComputation(base: number): number {
     let sum = 0;
     for (let i = 0; i < base * 10; i++) {
       sum += Math.sqrt(i);
     }
     return sum;
   }
   
   @Concurrent
   function parallelTask(base: number): number {
     let total = 0;
     for (let i = 0; i < base; i++) {
       total += i % 2 === 0 ? i : -i;
     }
     console.info('TaskPool thread calculation result: ', total);
     return total;
   }
   ```
