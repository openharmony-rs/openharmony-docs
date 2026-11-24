---
kits: ["ArkTS / Ark Programming Language"]
description: "Describes how to cancel TaskPool tasks in multithreading: Task objects do not support cross-thread transfer. Since API version 18, you can store the task ID in a Sendable object to cancel a task by its task ID in a child thread. A complete example is provided."
keywords: [cancel task, TaskPool, task ID, Sendable object, child thread cancellation, cross-thread transfer, multithreading]
doctype: guide
status: active
---

# Canceling Tasks in Multithreading with TaskPool
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @huanghello-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:38:49.441Z pushedAt=2026-11-12T08:35:24.617Z nl=1 -->

Since the task object [Task](../reference/apis-arkts/js-apis-taskpool.md#task) of the task pool [TaskPool](../reference/apis-arkts/js-apis-taskpool.md) does not support cross-thread transfer, tasks cannot be canceled directly in a child thread. Starting from API version 18, Task adds a task ID [property](../reference/apis-arkts/js-apis-taskpool.md#properties), which supports canceling tasks in a child thread through the task ID. Developers can store the task ID of a created task in a [Sendable object](./arkts-sendable.md), and when a task needs to be canceled, cancel the task in the child thread through the Sendable object. For details, see the following example.

1. Define a Sendable class and store the task ID in the class properties.

   <!-- @[define_sendable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/utils/Sendable.ets) --> 
   
   ``` TypeScript
   // sendable.ets
   @Sendable
   export class SendableTest {
     // Store the task ID
     private taskId: number = 0;
   
     constructor(id: number) {
       this.taskId = id;
     }
   
     public getTaskId(): number {
       return this.taskId;
     }
   }
   ```

2. Submit a delayed task to the TaskPool from the UI main thread and cancel it from a child thread.

   <!-- @[taskpool_cancel](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/pages/TaskpoolCancel.ets) -->
   
   ``` TypeScript
   // TaskpoolCancel.ets
   import { taskpool } from '@kit.ArkTS';
   import { SendableTest } from '../utils/Sendable';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { PromptAction } from '@kit.ArkUI';
   
   @Concurrent
   function cancel(send: SendableTest) {
     // Cancel the task by task ID in the child thread
     try {
       taskpool.cancel(send.getTaskId());
       console.info('cancel task finished');
     } catch (e) {
       console.error(`cancel failed, taskId: ${send.getTaskId()}, error: ${e.message}`);
     }
   }
   
   @Concurrent
   function delayed() {
     console.info('delayed task finished');
   }
   
   @Entry
   @Component
   struct TaskpoolCancel {
     @State message: string = 'CancelTaskpool';
     @State returnMessage: string = 'return...';
     @State promptAction: PromptAction = this.getUIContext().getPromptAction();
   
     build() {
       Row() {
         Column() {
           Button(this.message)
             .fontSize(25)
             .fontWeight(FontWeight.Bold)
             .onClick(async () => {
               let task = new taskpool.Task(delayed);
               taskpool.executeDelayed(2000, task).catch((e: BusinessError) => {
                 console.error(`taskpool execute error, message is: ${e.message}`);
                 // taskpool execute error, message is: taskpool:: task has been canceled.
               });
               let send = new SendableTest(task.taskId);
               taskpool.execute(cancel, send).then(() => {
                 this.returnMessage = 'Taskpool canceled!';
                 this.promptAction.showToast({ message: this.returnMessage });
               });
             })
           // ...
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
