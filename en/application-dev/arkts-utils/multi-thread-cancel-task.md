# Canceling Tasks in Multithreading with TaskPool
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

[Task](../reference/apis-arkts/js-apis-taskpool.md#task) objects of the [TaskPool](../reference/apis-arkts/js-apis-taskpool.md) cannot be passed across threads. Therefore, tasks cannot be canceled directly from child threads. Starting from API version 18, tasks have been enhanced with the [task ID](../reference/apis-arkts/js-apis-taskpool.md#properties), allowing tasks to be canceled in child threads using this ID. You can store the task ID of a created task in a [Sendable object](./arkts-sendable.md) and use this object to cancel the task from a child thread. For details, see the following example.

1. Define a Sendable class and store the task ID in the class properties.

   <!-- @[define_sendable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCasesSecond/entry/src/main/ets/utils/Sendable.ets) -->
   
   ``` TypeScript
   // sendable.ets
   @Sendable
   export class SendableTest {
     // Store the task ID.
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
     // Cancel the task in the child thread based on the task ID.
     taskpool.cancel(send.getTaskId());
     console.info('cancel task finished');
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
               taskpool.execute(cancel, send);
               this.returnMessage = 'Taskpool canceled!';
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
