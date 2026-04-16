# Worker同步调用宿主线程的接口
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

如果一个接口已在宿主线程中实现，Worker可以通过以下方式调用该接口。

以下示例展示了Worker同步调用宿主线程接口的方法，创建worker的方法可参考[创建worker的注意事项](worker-introduction.md#创建worker的注意事项)。

1. 首先，在宿主线程实现需要调用的接口，并创建Worker对象，在Worker对象上注册需要调用的对象。

   <!-- @[implement_child_thread_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/IconItemSource.ets) -->

   <!-- @[create_worker_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/WorkerCallGlobalUsage.ets) -->
   
   ``` TypeScript
   import worker from '@ohos.worker';
   import { IconItemSource } from './IconItemSource';
   
   // 创建Worker对象
   const workerInstance: worker.ThreadWorker = new worker.ThreadWorker('../workers/Worker');
   
   class PicData {
     public iconItemSourceList: IconItemSource[] = [];
   
     public setUp(): string {
       for (let index = 0; index < 20; index++) {
         const numStart: number = index * 6;
         // 此处循环使用6张图片资源
         this.iconItemSourceList.push(new IconItemSource('$media:startIcon', `item${numStart + 1}`));
         this.iconItemSourceList.push(new IconItemSource('$media:background', `item${numStart + 2}`));
         this.iconItemSourceList.push(new IconItemSource('$media:foreground', `item${numStart + 3}`));
         this.iconItemSourceList.push(new IconItemSource('$media:startIcon', `item${numStart + 4}`));
         this.iconItemSourceList.push(new IconItemSource('$media:background', `item${numStart + 5}`));
         this.iconItemSourceList.push(new IconItemSource('$media:foreground', `item${numStart + 6}`));
   
       }
       return 'setUpIconItemSourceList success!';
     }
   }
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'Hello World';
   
     build() {
       RelativeContainer() {
         Text(this.message)
           .id('HelloWorld')
           .fontSize(50)
           .fontWeight(FontWeight.Bold)
           .alignRules({
             center: { anchor: '__container__', align: VerticalAlign.Center },
             middle: { anchor: '__container__', align: HorizontalAlign.Center }
           })
           .onClick(() => {
             let picData = new PicData();
             // 在Worker上注册需要调用的对象
             workerInstance.registerGlobalCallObject('picData', picData);
             workerInstance.postMessage('run setUp in picData');
             this.message = 'success';
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```

2. 然后，在Worker中通过callGlobalCallObjectMethod接口可以调用宿主线程中的getMessage()方法。

   <!-- @[call_main_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/workers/Worker.ets) -->
   
   ``` TypeScript
   import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
   import { CopyEntry } from '../Sendable/CopyEntry';
   
   const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
   
   try {
     // 调用方法无入参
     let res: string = workerPort.callGlobalCallObjectMethod('picData', 'setUp', 0) as string;
     console.error('worker: ', res);
   } catch (error) {
     // 异常处理
     console.error('worker: error code is ' + error.code + ' error message is ' + error.message);
   }
   ```
