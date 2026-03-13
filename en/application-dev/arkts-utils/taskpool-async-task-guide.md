# Specifying Task Concurrency with TaskPool
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

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
     // Collect and process data.
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
               // Create an asynchronous queue with a concurrency level of 5 and a queue capacity of 5. If the number of added tasks exceeds 5, the task at the head of the waiting list is discarded.
               let asyncRunner:taskpool.AsyncRunner = new taskpool.AsyncRunner('async', 5, 5);
               // Trigger a collection task.
               for (let i = 0; i < 20; i++) {
                 let task:taskpool.Task = new taskpool.Task(`async${i}`,collectFrame);
                 asyncRunner.execute(task).then(() => {
                   console.info('the current task name is ' + task.name);
                 }).catch((e:BusinessError) => {
                   console.error('async: error is ' + e);
                 });
               }
               console.info('asyncRunner task finished');
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
