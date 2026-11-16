---
kits: ["ArkTS / Ark Programming Language"]
description: "Describes how a Worker synchronously calls a host thread interface: implement the interface in the host thread and register the call object, and the Worker thread initiates a synchronous call through callGlobalCallObjectMethod and obtains the return result. This applies to scenarios where a child thread reuses capabilities already implemented in the main thread."
keywords: [synchronous call, callGlobalCallObjectMethod, host thread interface, Worker, object registration, interface reuse, cross-thread call]
doctype: guide
status: active
---

# Synchronous Calls to Host Thread Interfaces from Worker
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:53:40.960Z pushedAt=2026-11-12T13:44:02.110Z nl=1 -->

This topic describes the approach that Worker uses to call an interface that is already implemented in the host thread.

The following example shows how a Worker synchronously calls a host thread interface. For details about how to create a Worker, see [Notes on Creating a Worker](worker-introduction.md#precautions-for-creating-a-worker).

1. Implement the interface in the host thread and create a Worker object. Register the interface to be called on the Worker object.

   <!-- @[create_worker_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/managers/WorkerCallGlobalUsage.ets) -->
   
   ``` TypeScript
   import { MessageEvents, worker } from '@kit.ArkTS';
      
      class TestObj {
        public getMessage(): string {
          return 'this is a message from TestObj';
        }
      
        public static testObj: TestObj = new TestObj();
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
                  // Create a Worker object.
                  const workerInstance: worker.ThreadWorker = new worker.ThreadWorker("entry/ets/workers/Worker.ets");
                  // Register the object to be called on the Worker.
                  workerInstance.registerGlobalCallObject('testObj', TestObj.testObj);
                  workerInstance.onmessage = (e: MessageEvents): void => {
                    // Receive the result from the Worker child thread.
                    console.info('mainThread: ' + e.data);
                    // Destroy the Worker.
                    workerInstance.terminate();
                  }
                  workerInstance.postMessage('start');
                })
            }
            .width('100%')
          }
          .height('100%')
        }
      }
   ```

2. Then, in the Worker, call the getMessage() method in the host thread through the [callGlobalCallObjectMethod](../reference/apis-arkts/js-apis-worker.md#callglobalcallobjectmethod11) interface.

   <!-- @[call_main_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationScenario/entry/src/main/ets/workers/Worker.ets) -->
   
   ``` TypeScript
   import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
   
   const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
   
   workerPort.onmessage = (e: MessageEvents) => {
     if (e.data === 'start') {
       try {
         // Call the method.
         let res: string = workerPort.callGlobalCallObjectMethod('testObj', 'getMessage', 0) as string;
         if (res === 'this is a message from TestObj') {
           workerPort.postMessage('run function success.');
         }
       } catch (error) {
         // Handle exceptions.
         console.error('worker: error code is ' + error.code + ' error message is ' + error.message);
       }
     }
   
     // ...
   }
   ```
