# 自定义Native Transferable对象的多线程操作场景
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

在ArkTS应用开发中，有很多场景需要将ArkTS对象与Native对象进行绑定。ArkTS对象将数据写入Native对象，Native对象再将数据写入目的地。例如，将ArkTS对象中的数据写入C++数据库场景。

Native Transferable对象有两种模式：共享模式和转移模式。本示例将详细说明如何实现这两种模式。

1. Native实现各项功能。

   <!-- @[define_customNativeObject](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCaseTransferable/entry/src/main/cpp/napi_init.cpp) -->  

2. 在ArkTS中声明接口。

   <!-- @[declare_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCaseTransferable/entry/src/main/cpp/types/libentry/Index.d.ts) -->    

3. ArkTS对象调用Native侧实现的各项功能。

   <!-- @[load_trans](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCaseTransferable/entry/src/main/ets/pages/TransferableCase.ets) --> 

   在转移模式下，跨线程传递后，原来的ArkTS对象与Native对象解绑，因此不能继续访问。示例如下：
   ```ts
   import testNapi from 'libentry.so';
   import { taskpool } from '@kit.ArkTS';
   
   @Concurrent
   function getAddress() {
     let address: number = testNapi.getAddress();
     console.info("taskpool:: address is " + address);
   }
   
   @Concurrent
   function store(a:number, b:number, c:number) {
     let size:number = testNapi.getSetSize();
     console.info("set size is " + size + " before store");
     testNapi.store(a);
     testNapi.store(b);
     testNapi.store(c);
     size = testNapi.getSetSize();
     console.info("set size is " + size + " after store");
   }
   
   @Concurrent
   function erase(a:number) {
     let size:number = testNapi.getSetSize();
     console.info("set size is " + size + " before erase");
     testNapi.erase(a);
     size = testNapi.getSetSize();
     console.info("set size is " + size + " after erase");
   }
   
   @Concurrent
   function clear() {
     let size:number = testNapi.getSetSize();
     console.info("set size is " + size + " before clear");
     testNapi.clear();
     size = testNapi.getSetSize();
     console.info("set size is " + size + " after clear");
   }
   
   // 转移模式
   async function test(): Promise<void> {
     // setTransferDetached 设置为true，表示传输方式为转移模式
     testNapi.setTransferDetached(true);
     let address:number = testNapi.getAddress();
     console.info("host thread address is " + address);
   
     let task1 = new taskpool.Task(getAddress, testNapi);
     await taskpool.execute(task1);
     
     let task2 = new taskpool.Task(store, 1, 2, 3);
     await taskpool.execute(task2);
   
     let task3 = new taskpool.Task(store, 4, 5, 6);
     await taskpool.execute(task3);

     // 由于已经设置了转移模式，且testNapi已跨线程传递，所以主线程无法继续访问到Native对象的值
     let size:number = testNapi.getSetSize();
     // 输出的日志为“host thread size is undefined”
     console.info("host thread size is " + size);
   
     let task4 = new taskpool.Task(erase, 3);
     await taskpool.execute(task4);
   
     let task5 = new taskpool.Task(erase, 5);
     await taskpool.execute(task5);
   
     let task6 = new taskpool.Task(clear);
     await taskpool.execute(task6);
   }
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'Hello World';
   
     build() {
       Row() {
         Column() {
           Text(this.message)
             .fontSize($r('app.float.page_text_font_size'))
             .fontWeight(FontWeight.Bold)
             .onClick(() => {
               test();
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

   在共享模式下，跨线程传递后，原来的ArkTS对象还可以继续访问Native对象。示例如下：

   <!-- @[load_share](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCaseTransferable/entry/src/main/ets/pages/ShareCase.ets) --> 
