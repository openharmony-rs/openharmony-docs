# Asynchronous Waiting
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @dwhuawei-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=5f2bc820d02c0fb06b1bd1ea2345bc0bf048c408 translatedAt=2026-11-04T09:01:40.158Z pushedAt=2026-11-04T09:24:35.364Z nl=1 -->

ArkTS introduces the wait and wake-up capability for asynchronous tasks to solve the timing control problem of multithreaded tasks. Asynchronous tasks implement the wait and wake-up mechanism through the [ConditionVariable](../reference/apis-arkts/arkts-apis-arkts-utils-locks.md#conditionvariable18) object, which supports cross-thread reference passing.

The ArkTS language supports asynchronous operations. Starting from API version 18, it supports the wait and wake-up feature for asynchronous tasks. When an asynchronous task receives a wake-up notification or the wait times out, it continues execution.

> **Note:**
>
> Asynchronous methods must be marked with async, and await can be used when calling them to ensure correct timing.

## Usage Example

The following example demonstrates how to control asynchronous task waiting and awakening using [Sendable](arkts-sendable.md) objects across threads.

   <!-- @[sendable_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/AsynchronousWaiting/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { ArkTSUtils, taskpool } from '@kit.ArkTS';
   
   @Concurrent
   function notifyAll(conditionVariable: ArkTSUtils.locks.ConditionVariable) {
     console.info(`TaskPool Thread notifyAll`);
     conditionVariable.notifyAll();
   }
   
   @Concurrent
   function notifyOne(conditionVariable: ArkTSUtils.locks.ConditionVariable) {
     console.info(`TaskPool Thread notifyOne`);
     conditionVariable.notifyOne();
   }
   
   @Concurrent
   async function wait(conditionVariable: ArkTSUtils.locks.ConditionVariable) {
     await conditionVariable.wait();
     console.info(`TaskPool Thread Wait: success`);
   }
   
   @Concurrent
   async function waitFor(conditionVariable: ArkTSUtils.locks.ConditionVariable) {
     await conditionVariable.waitFor(3000);
     console.info(`TaskPool Thread WaitFor: success`);
   }
   
   @Entry
   @Component
   struct Index {
     @State message: string | ResourceStr = $r('app.string.AsyncButton'); // Load the resource. Customize it based on the actual project resources.
   
     build() {
       Row() {
         Column() {
           Button(this.message)
             .fontSize(25)
             .fontWeight(FontWeight.Bold)
             .onClick(async () => {
               // Create a conditionVariable object.
               const conditionVariable: ArkTSUtils.locks.ConditionVariable = new ArkTSUtils.locks.ConditionVariable();
               // Pass the conditionVariable instance to the wait thread.
               taskpool.execute(wait, conditionVariable);
               // Pass the conditionVariable instance to the notifyAll thread to wake up the wait thread. Log "TaskPool Thread Wait: success".
               await taskpool.execute(notifyAll, conditionVariable);
               // Pass the conditionVariable instance to the waitFor thread.
               taskpool.execute(waitFor, conditionVariable);
               // Pass the conditionVariable instance to the notifyOne thread to wake up the waitFor thread. Log "TaskPool Thread WaitFor: success".
               await taskpool.execute(notifyOne, conditionVariable);
   
               // Create a conditionVariable object with a name.
               const conditionVariableRequest: ArkTSUtils.locks.ConditionVariable =
                 ArkTSUtils.locks.ConditionVariable.request('Request1');
               // Pass the conditionVariableRequest instance to the wait thread.
               taskpool.execute(wait, conditionVariableRequest);
               // Pass the conditionVariableRequest instance to the notifyAll thread to wake up the wait thread. Log "TaskPool Thread Wait: success".
               await taskpool.execute(notifyAll, conditionVariableRequest);
               // Pass the conditionVariableRequest instance to the waitFor thread.
               taskpool.execute(waitFor, conditionVariableRequest);
               // Pass the conditionVariableRequest instance to the notifyOne thread to wake up the waitFor thread. Log "TaskPool Thread WaitFor: success".
               await taskpool.execute(notifyOne, conditionVariableRequest);
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```


