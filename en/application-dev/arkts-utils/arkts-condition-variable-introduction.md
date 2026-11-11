---
kits: ["ArkTS"]
description: "Introduces the ArkTS asynchronous wait (ConditionVariable) capability, which implements the wait and wake-up mechanism for multithreaded asynchronous tasks through the ConditionVariable object. It supports wait, waitFor timeout waiting, and notifyAll and notifyOne wake-up operations to solve cross-thread task timing control problems."
keywords: [asynchronous wait, ConditionVariable, wait and wake-up, multithreaded timing control, notifyAll, notifyOne, wait, waitFor, timeout wait]
doctype: guide
status: active
---

# Asynchronous Waiting
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @dwhuawei-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=d802165dde49a731f0fcacc5a6108aec607634d1 translatedAt=2026-11-06T10:15:46.386Z pushedAt=2026-11-09T08:50:43.164Z nl=1 -->

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
     @State message: string | ResourceStr = $r('app.string.AsyncButton'); // Load the resource. You can customize it based on the actual project resource.
   
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
               // Pass the conditionVariable instance to the notifyAll thread to wake up the wait thread. The log outputs "TaskPool Thread Wait: success".
               await taskpool.execute(notifyAll, conditionVariable);
               // Pass the conditionVariable instance to the waitFor thread.
               taskpool.execute(waitFor, conditionVariable);
               // Pass the conditionVariable instance to the notifyOne thread to wake up the waitFor thread. The log outputs "TaskPool Thread WaitFor: success".
               await taskpool.execute(notifyOne, conditionVariable);
   
               // Create a conditionVariable object with a name.
               const conditionVariableRequest: ArkTSUtils.locks.ConditionVariable =
                 ArkTSUtils.locks.ConditionVariable.request('Request1');
               // Pass the conditionVariableRequest instance to the wait thread.
               taskpool.execute(wait, conditionVariableRequest);
               // Pass the conditionVariableRequest instance to the notifyAll thread to wake up the wait thread. The log outputs "TaskPool Thread Wait: success".
               await taskpool.execute(notifyAll, conditionVariableRequest);
               // Pass the conditionVariableRequest instance to the waitFor thread.
               taskpool.execute(waitFor, conditionVariableRequest);
               // Pass the conditionVariableRequest instance to the notifyOne thread to wake up the waitFor thread. The log outputs "TaskPool Thread WaitFor: success".
               await taskpool.execute(notifyOne, conditionVariableRequest);
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```


