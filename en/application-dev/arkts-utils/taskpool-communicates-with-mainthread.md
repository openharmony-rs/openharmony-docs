# Communication Between the TaskPool Task and Host Thread
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=57b7b329f3b5c5d9978489bcd766a9d7a36f312c translatedAt=2026-11-04T09:37:31.304Z pushedAt=2026-11-04T09:40:05.134Z nl=1 -->

When a task needs to do more than just return a final result—such as periodically updating the host thread on its status, reporting data changes, or returning large volumes of data in segments (for example, fetching large datasets from a database)—you can use the approach described in this topic.

The following example uses multiple image loading tasks that provide real-time updates to illustrate the process.

In the Task to be executed, add the sendData() API to send messages to the host thread. On the host thread, receive messages through the onReceiveData() API. In this way, the host thread can receive the data sent by the Task through the notice() API.

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

   <!-- @[implement_child_thread_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/TaskSendDataUsage.ets) --> 
   
   ``` TypeScript
   import { taskpool } from '@kit.ArkTS';
   import { IconItemSource } from './IconItemSource';
   import { BusinessError } from '@kit.BasicServicesKit';
   // Implement the method for receiving Task messages.
   function notice(data: number): void {
     console.info('Data loaded in the child thread, total images loaded: ', data);
   }
   
   // Notify the host thread of information in real time through the Task's sendData method.
   @Concurrent
   export function loadPictureSendData(count: number): IconItemSource[] {
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
   
       taskpool.Task.sendData(iconItemSourceList.length);
     }
     return iconItemSourceList;
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
               let iconItemSourceList: IconItemSource[];
               let loadPictureTask: taskpool.Task = new taskpool.Task(loadPictureSendData, 30);
               // Use notice to receive messages from the task.
               loadPictureTask.onReceiveData(notice);
               taskpool.execute(loadPictureTask).then((res: object) => {
                 iconItemSourceList = res as IconItemSource[];
                 this.message = 'success';
               }).catch((e: BusinessError) => {
                 this.message = 'failed';
                 console.error(`taskpool: execute: Code: ${e.code}, message: ${e.message}`);
               })
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
