---
kits: ["ArkTS / Ark Programming Language"]
description: "Introduces the capability of a Worker to perform queue-jumping message communication with the host thread: postMessageAtFront inserts a message at the head of the host thread's message queue for priority processing, which is suitable for scenarios where high-priority messages require immediate response. It also explains the queue-jumping mechanism and provides a complete usage example."
keywords: [message queue-jumping, postMessageAtFront, message queue, high-priority message, priority processing, Worker communication, immediate response, multithreading]
doctype: guide
status: active
---

# Queue-Jumping Message Communication from Worker to Host Thread
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-02T14:23:45.906Z pushedAt=2026-11-03T04:23:28.345Z nl=1 -->

## When to Use

In Worker multithreaded development, when a Worker thread sends messages to the host thread (the main thread or another Worker thread) through [postMessage](../reference/apis-arkts/js-apis-worker.md#postmessage9-2), the messages are queued and processed in the order they are sent. When the host thread is busy, a large number of pending messages may accumulate in the message queue, causing some messages that need to be processed in a timely manner (such as user interaction responses and critical state updates) to fail to be executed promptly.

To address the preceding scenario, starting from API version 26.0.0, ArkTS provides the [postMessageAtFront](../reference/apis-arkts/js-apis-worker.md) API, which allows a Worker thread to send a queue-jumping message to the host thread so that the message is inserted at the head of the message queue of the corresponding priority and is therefore processed earlier.

## Queue-Jumping Mechanism

- When a Worker thread sends a message to the host thread, queue-jumping is supported, and the message can be sent by [Priority](../reference/apis-arkts/js-apis-worker.md).
- Queue-jumping is implemented by inserting the message at the head of the message queue of the corresponding priority.
- The higher the priority, the earlier the message is processed by the host thread. The processing order follows the priority scheduling rule: IMMEDIATE > HIGH > LOW > IDLE.
  | Priority | Value | Description |
  | --- | --- | --- |
  | IMMEDIATE | 1 | Immediate execution priority, processed before HIGH priority. |
  | HIGH | 2 | High priority, the same priority as ordinary postMessage messages. |
  | LOW | 3 | Low priority, processed before IDLE priority. |
  | IDLE | 4 | Background priority, processed only when there are no messages of other priorities. |
- For messages with the same priority, the message at the head of the message queue is processed first by the host thread.

## Samples

The following example simulates a busy host thread to demonstrate how the Worker thread sends a queue-jumping message to the host thread through the postMessageAtFront() API.

1. Create a Worker object in the host thread, and send and receive messages.

   In this example, you can click the "Trigger Message Sending" button to send a message to the Worker thread.

   <!-- @[parent_worker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/MultithreadedConcurrency/WorkerPostAtFront/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { MessageEvents, worker } from '@kit.ArkTS';
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'Hello World';
     @State workerObject: worker.ThreadWorker | null = null;
     aboutToAppear(): void {
       this.workerObject = new worker.ThreadWorker('entry/ets/workers/Worker.ets');
       this.workerObject.onmessage = (e: MessageEvents): void => {
         // Simulate a time-consuming operation. Each received message is processed for 100 ms to make messages queue up.
         let start = new Date().getTime();
         while (new Date().getTime() - start < 100) {
           continue;
         }
         let res: string = e.data as string;
         console.info('result is: ' + JSON.stringify(res));
       }
     }
     build() {
       Row() {
         Column({space: 20}) {
           Text(this.message)
             .fontSize(50)
             .fontWeight(FontWeight.Bold)
           Button('Trigger message sending')
             .fontSize(50)
             .onClick(()=>{
               if (this.workerObject != null) {
                 this.workerObject.postMessage('normal');
               }
             })
           Button('Release worker')
             .fontSize(50)
             .onClick(()=>{
               if (this.workerObject != null) {
                 this.workerObject.terminate();
                 this.workerObject = null;
               }
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

2. Send a queue-jumping message in the Worker thread.

   After receiving the message from the host thread, the Worker thread sends a normal message and a queue-jumping message.

   <!-- @[child_worker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/MultithreadedConcurrency/WorkerPostAtFront/entry/src/main/ets/workers/Worker.ets) -->
   
   ``` TypeScript
   import { MessageEvents, ThreadWorkerGlobalScope, worker, Priority } from '@kit.ArkTS';
   
   const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
   
   workerPort.onmessage = (e: MessageEvents) => {
     // Send multiple messages to make them queue up.
     for (let i = 0; i < 10; i++) {
       // Use ordinary message sending to process in the default queuing order.
       workerPort.postMessage('normal message.');
     }
     // HIGH priority: the same priority as ordinary messages, inserted at the head of the queue to make the message execute earlier.
     workerPort.postMessageAtFront?.('atFront high message', Priority.HIGH);
   }
   ```
