---
kits: ["ArkTS / ArkTS Programming Language"]
description: "Provides development guidance for the TaskPool task concurrency scenario: uses the AsyncRunner asynchronous queue to control concurrent task execution, demonstrates the implementation using camera preview stream data collection as an example, and applies to high-frequency task scenarios such as network requests, video stream processing, and database operations."
keywords: [task concurrency, asynchronous queue, AsyncRunner, TaskPool, camera preview stream, video stream processing, resource overload]
doctype: guide
status: active
---

# Specifying Task Concurrency with TaskPool
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:47:57.962Z pushedAt=2026-11-09T09:09:40.524Z nl=1 -->

TaskPool supports using asynchronous queues to control task concurrency, effectively preventing resource overload and reducing task blocking. It is well-suited for scenarios such as network requests, video stream processing, and database operations.

This section describes how to use TaskPool to create [asynchronous queues](../reference/apis-arkts/js-apis-taskpool.md#asyncrunner18). It uses the operation of collection and processing of camera preview stream data as an example.

This operation is frequent and time consuming. If the camera captures data too quickly, earlier frames are discarded to ensure only the most recent frame is processed.

1. Import the required modules.
   <!-- @[taskpool_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/pages/TaskpoolAsyncLevel.ets) -->   
   
   ``` TypeScript
   // TaskpoolAsyncLevel.ets
   import { taskpool } from '@kit.ArkTS';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { PromptAction } from '@kit.ArkUI';
   ```

2. Define a time-consuming task.

   <!-- @[collect_frame](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/pages/TaskpoolAsyncLevel.ets) -->
   
   ``` TypeScript
   // TaskpoolAsyncLevel.ets
   @Concurrent
   function collectFrame() {
     // Collect data and process it.
     // Simulate the processing task, which is time consuming and lasts for 30 seconds.
     let t = new Date().getTime()
     while (new Date().getTime() - t < 30000) {
       continue;
     }
     console.info('collectFrame finished');
   }
   ```

3. Create an asynchronous queue and execute the collection task.

   <!-- @[trigger_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/pages/TaskpoolAsyncLevel.ets) --> 
   
   ``` TypeScript
   // TaskpoolAsyncLevel.ets
   @Entry
   @Component
   struct TaskpoolAsyncLevel {
     @State message: string = 'Trigger the collection task.';
     @State returnMessage: string = 'return...';
     @State promptAction: PromptAction = this.getUIContext().getPromptAction();
     
     build() {
       Row() {
         Column() {
           Button(this.message)
             .fontSize(50)
             .fontWeight(FontWeight.Bold)
             .onClick(async () => {
               // Create an asynchronous queue with a concurrency of 5 and a waiting queue size of 5. When the number of added tasks exceeds 5, the task at the head of the waiting list is discarded.
               let asyncRunner: taskpool.AsyncRunner = new taskpool.AsyncRunner('async', 5, 5);
               // Trigger a collection task.
               let promises: Promise<void>[] = [];
               for (let i = 0; i < 20; i++) {
                 let task: taskpool.Task = new taskpool.Task(`async${i}`, collectFrame);
                 let p: Promise<void> = asyncRunner.execute(task).then(() => {
                   console.info('the current task name is ' + task.name);
                 }).catch((e: BusinessError) => {
                   console.error('async: error is ' + e);
                 });
                 promises.push(p);
               }
               // Wait for all tasks to complete before executing subsequent statements.
               await Promise.allSettled(promises);
               console.info('asyncRunner tasks submitted');
               this.returnMessage = 'asyncRunner task finished';
               this.promptAction.showToast({ message: this.returnMessage });
             })
           // ...
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
