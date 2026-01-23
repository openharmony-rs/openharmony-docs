# 多级Worker间高性能消息通信
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

多级[Worker](worker-introduction.md)（即通过父Worker创建子Worker的机制形成层级线程关系）间通信是一种常见的需求，由于Worker线程生命周期由用户自行管理，因此需要注意多级Worker生命周期的正确管理，建议开发者确保销毁父Worker前先销毁所有子Worker。

本文介绍如何在多级Worker间实现高性能消息通信。高性能消息通信的关键在于[Sendable对象](arkts-sendable.md)，结合[postMessageWithSharedSendable接口](../reference/apis-arkts/js-apis-worker.md#postmessagewithsharedsendable12)，可以实现线程间高性能的对象传递。例如，在数据克隆场景中，假设有一个父Worker和两个子Worker。父Worker负责创建子Worker，并向子Worker发送数据克隆任务。子Worker接收任务并执行数据克隆操作，完成后将克隆结果返回给父Worker。

1. 在ets文件夹下新建文件夹Sendable，并准备一个Sendable类CopyEntry，封装克隆任务数据。

   <!-- @[copy_entry_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/Sendable/CopyEntry.ets) -->     

2. 创建两个Worker文件，DevEco Studio支持一键生成Worker，在对应的{moduleName}目录下任意位置，单击鼠标右键 &gt; New &gt; Worker，即可自动生成Worker的模板文件及配置信息。本文以创建“ParentWorker”（父Worker）和“ChildWorker”（子Worker）为例。父Worker负责分发克隆任务并判断任务全部完成后关闭子Worker与父Worker；子Worker负责接收任务并执行数据克隆操作，并在任务完成后通知父Worker。
  
   <!-- @[parent_worker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/workers/ParentWorker.ets) -->      
   
   <!-- @[child_worker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/workers/ChildWorker.ets) -->    

3. 在UI主线程页面，创建父Worker并准备克隆任务所需的数据，准备完成后将数据发送给父Worker。

   <!-- @[multi_worker_high_performance_communication](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/WorkerPostMessageSendable.ets) -->   
   
   ``` TypeScript
   // Index.ets
   import { worker, collections } from '@kit.ArkTS';
   import { CopyEntry } from '../Sendable/CopyEntry'
   
   function promiseCase() {
     let p: Promise<void> = new Promise<void>((resolve: Function, reject: Function) => {
       setTimeout(() => {
         resolve();
       }, 100);
     });
     return p;
   }
   
   async function postMessageTest() {
     let ss = new worker.ThreadWorker('entry/ets/workers/ParentWorker.ets');
     let isTerminate = false;
     ss.onexit = () => {
       isTerminate = true;
     }
     let array = new collections.Array<CopyEntry>();
     // 准备数据
     for (let i = 0; i < 4; i++) {
       if (i % 2 == 0) {
         array.push(new CopyEntry('copy1', 'file://copy1.txt'));
       } else {
         array.push(new CopyEntry('copy2', 'file://copy2.txt'));
       }
     }
     // 给Worker线程发送消息
     ss.postMessageWithSharedSendable(array);
     while (!isTerminate) {
       await promiseCase();
     }
     console.info('Worker线程已退出');
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
               postMessageTest();
               // ...
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
