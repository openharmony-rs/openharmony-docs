# 多线程取消TaskPool任务场景
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

由于任务池[TaskPool](../reference/apis-arkts/js-apis-taskpool.md)的任务对象[Task](../reference/apis-arkts/js-apis-taskpool.md#task)不支持跨线程传递，无法在子线程中直接取消任务。从 API version 18 开始，Task新增了[任务ID](../reference/apis-arkts/js-apis-taskpool.md#属性)属性，支持通过任务ID在子线程中取消任务。开发者可将已创建任务的任务ID存储在[Sendable对象](./arkts-sendable.md)中，需要取消任务时，通过Sendable对象在子线程中取消任务。详情可参考以下示例。

1. 定义一个Sendable类，在类属性中存储任务ID。

   ```ts
   // sendable.ets

   @Sendable
   export class SendableTest {
    // 存储任务ID
     private taskId: number = 0;

     constructor(id: number) {
       this.taskId = id;
     }

     public getTaskId(): number {
       return this.taskId;
     }
   }
   ```

2. 在UI主线程向TaskPool提交一个延时任务，并在子线程取消该任务。

   ```ts
   // Index.ets

   import { taskpool } from '@kit.ArkTS';
   import { SendableTest } from './sendable';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   @Concurrent
   function cancel(send: SendableTest) {
     // 在多线程中通过任务ID取消任务
     taskpool.cancel(send.getTaskId());
     console.info("cancel task finished");
   }
   
   @Concurrent
   function delayed() {
     console.info("delayed task finished");
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
             .onClick(async () => {
               let task = new taskpool.Task(delayed);
               taskpool.executeDelayed(2000, task).catch((e: BusinessError) => {
                 console.error(`taskpool execute error, message is: ${e.message}`); // taskpool execute error, message is: taskpool:: task has been canceled
               });
               let send = new SendableTest(task.taskId);
               taskpool.execute(cancel, send);
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```