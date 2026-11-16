# Using TaskPool for Independent Time-Consuming Tasks
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=5f2bc820d02c0fb06b1bd1ea2345bc0bf048c408 translatedAt=2026-11-04T09:18:43.885Z pushedAt=2026-11-04T12:46:21.154Z nl=1 -->

For a time-consuming task that runs independently, you only need to return the result to the host thread after the task is executed. You can use the approach described in this topic.

This example uses image loading to illustrate the process.

1. Implement the task to be executed in a child thread.

   <!-- @[implement_child_thread_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/IconItemSource.ets) -->
   
   ``` TypeScript
   export class IconItemSource {
     image: string | Resource = '';
     text: string | Resource = '';
   
     constructor(image: string | Resource = '', text: string | Resource = '') {
       this.image = image;
       this.text = text;
     }
   }
   ```

   <!-- @[implement_child_thread_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/IndependentTask.ets) -->
   
   ``` TypeScript
   import { IconItemSource } from './IconItemSource';
   
   // The method executed in a Task must be annotated with @Concurrent; otherwise, it cannot be called properly.
   @Concurrent
   export function loadPicture(count: number): IconItemSource[] {
     let iconItemSourceList: IconItemSource[] = [];
     // Traverse and add data of 6*count IconItems.
     for (let index = 0; index < count; index++) {
       const numStart: number = index * 6;
       // Use 6 image resources in the loop here.
       iconItemSourceList.push(new IconItemSource('$media:startIcon', `item${numStart + 1}`));
       iconItemSourceList.push(new IconItemSource('$media:background', `item${numStart + 2}`));
       iconItemSourceList.push(new IconItemSource('$media:foreground', `item${numStart + 3}`));
       iconItemSourceList.push(new IconItemSource('$media:startIcon', `item${numStart + 4}`));
       iconItemSourceList.push(new IconItemSource('$media:background', `item${numStart + 5}`));
       iconItemSourceList.push(new IconItemSource('$media:foreground', `item${numStart + 6}`));
     }
     return iconItemSourceList;
   }
   ```

2. Use the **execute** method of TaskPool to execute the task, that is, to load the images.

   <!-- @[execute_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/IndependentTimeConsumingTask.ets) -->
   
   ``` TypeScript
   import { taskpool } from '@kit.ArkTS';
   import { IconItemSource } from './IconItemSource';
   import { loadPicture } from './IndependentTask';
   
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
               let iconItemSourceList: IconItemSource[] = [];
               // Create a Task.
               let loadPictureTask: taskpool.Task = new taskpool.Task(loadPicture, 30);
               // Execute the Task and return the result.
               taskpool.execute(loadPictureTask).then((res: object) => {
                 // Execution result of the loadPicture method.
                 iconItemSourceList = res as IconItemSource[];
                 this.message = 'success';
               }).catch(() => {
                 console.error(`Failed to execute taskpool.`);
                 this.message = 'fail';
               })
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
