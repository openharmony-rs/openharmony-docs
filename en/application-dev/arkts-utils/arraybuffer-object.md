---
kits: ["ArkTS"]
description: "Describes the cross-thread transfer modes of ArrayBuffer objects: copy transfer duplicates binary data before passing it, while move transfer transfers memory ownership to avoid copy overhead. This is suitable for efficiently passing large contiguous binary data such as images and audio across threads."
keywords: [ArrayBuffer, binary data, copy transfer, move transfer, memory ownership, cross-thread transfer, contiguous memory data]
doctype: guide
status: active
---

# ArrayBuffer Object
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=3621e01243307de1ff4f06e11dd17a074cf484af translatedAt=2026-11-06T10:23:51.521Z pushedAt=2026-11-11T07:58:13.318Z nl=1 -->

An ArrayBuffer consists of two components: the underlying native memory area that stores data, and the JS object wrapper that encapsulates operations. This JS object wrapper is allocated on the virtual machine's local heap. When passed across threads, the JS object wrapper needs to be serialized and deserialized for pass-by-copy, whereas the native memory area can be transferred in two ways: pass-by-copy and pass-by-transfer.

When pass-by-copy (recursive traversal) is used for the native memory area, both threads can independently access the ArrayBuffer object after the transmission. This method requires rebuilding the JS object wrapper and copying the native memory area, which is inefficient. The following figure shows the communication process.

![copy_transfer](figures/copy_transfer.png)

When Native memory is transferred using the transfer method, the original thread can no longer use this ArrayBuffer object after the transfer. During cross-thread transfer, only the JS shell needs to be rebuilt, and the Native memory does not need to be copied, thereby improving efficiency. The communication process is shown in the following figure:

![transfer](figures/transfer.png)

ArrayBuffer is often used to represent binary resources such as images. In application development, processing images (such as adjusting brightness, saturation, and size) can be time-consuming. To avoid blocking the UI main thread for a long time, you can pass the image to a child thread for processing. Passing the ArrayBuffer using the transfer method can improve transfer performance, but the original thread can no longer access the ArrayBuffer object. If both threads need to access the object, only the copy method can be used. Otherwise, the transfer method is recommended to improve performance.

The following sections describe how to transfer images across ArkTS threads using both methods.

## Pass-by-Copy

In ArkTS, when TaskPool passes ArrayBuffer data, the transfer method is used by default. By calling the [setTransferList()](../reference/apis-arkts/js-apis-taskpool.md#settransferlist10) API, you can specify that part of the data is passed using the transfer method, while the rest of the data can be switched to the copy method.

First, implement an API for processing ArrayBuffer. The API is executed in a task.

Then, pass the ArrayBuffer data to the task by copy and process it.

Finally, the UI main thread receives the ArrayBuffer data returned after the task is executed, combines the data, and displays it.

<!-- @[copy_arraybuffer_transfer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/CommunicationObjects/entry/src/main/ets/managers/ArrayBufferObject.ets) --> 

``` TypeScript
import { taskpool } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Processing function executed in a Task, used to process ArrayBuffer data
@Concurrent
function adjustImageValue(arrayBuffer: ArrayBuffer): ArrayBuffer {
  // Operate on arrayBuffer. The return value is transferred by default.
  return arrayBuffer;
}

/*
 * Create a Task to pass an ArrayBuffer into the Task for execution
 * isParamsByCopy controls whether the ArrayBuffer is passed by "copy" or "transfer"
 */
function createImageTask(arrayBuffer: ArrayBuffer, isParamsByCopy: boolean): taskpool.Task {
  let task: taskpool.Task = new taskpool.Task(adjustImageValue, arrayBuffer);
  if (isParamsByCopy) {
    // Pass an empty array []. All arrayBuffer parameters are passed by copy.
    try {
      task.setTransferList([]);
    } catch (err) {
      hilog.error(0x0000, 'testTag', 'Failed to set transferList. Cause: %{public}s', JSON.stringify(err));
    }
  }
  return task;
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
          // Create the ArrayBuffer to be processed and split it by taskNum
          let taskNum = 4;
          let arrayBuffer = new ArrayBuffer(1024 * 1024);
          let taskPoolGroup = new taskpool.TaskGroup();
          // Create taskNum Tasks
          for (let i: number = 0; i < taskNum; i++) {
            let arrayBufferSlice: ArrayBuffer =
              arrayBuffer.slice(arrayBuffer.byteLength / taskNum * i, arrayBuffer.byteLength / taskNum * (i + 1));
            // When isParamsByCopy is true, copy-mode transfer can be implemented
            taskPoolGroup.addTask(createImageTask(arrayBufferSlice, true));
          }
          // Execute the Task. The UI main thread receives the processed result.
          taskpool.execute(taskPoolGroup).then((data) => {
            // Concatenate and further process the ArrayBuffer data returned by each Task (i.e., data, which here is an array of length 4 containing 4 groups of arrayBufferSlice). Specific operations are not listed here.
            // ...
            this.message = 'success';
          }).catch((e: BusinessError) => {
            this.message = 'fail';
            console.error(`taskpool: execute task: code: ${e.code}, message: ${e.message}`);
          })
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## Pass-by-Transfer

In TaskPool, when passing ArrayBuffer data, the transfer method is used by default, and the original thread can no longer use the ArrayBuffer that has been transferred to the child thread. Based on the preceding example, remove the `task.setTransferList()` API call, that is, pass false as the second parameter of createImageTask, to implement transfer-method passing.

## Transfer Modes of ArrayBuffer in Worker Scenarios

Unlike TaskPool, which uses the transfer mode by default, when passing an ArrayBuffer through [postMessage](../reference/apis-arkts/js-apis-worker.md#postmessage9-1) in a Worker scenario, the transfer mode is determined by whether the ArrayBuffer is included in the transfer list: if the ArrayBuffer is added to the transfer list, it is passed in transfer mode; otherwise, it is passed in copy transfer mode.

When passing large binary data (such as images and raw audio/video data) to a Worker for processing, if the host thread no longer needs to access the original data while the Worker is processing it, you are advised to put the ArrayBuffer into the transfer list (`transfer`) and pass it in transfer mode to avoid the doubled memory usage and copy overhead caused by deep copy. The following is an example:

<!-- @[worker_send](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/CommunicationObjects/entry/src/main/ets/managers/WorkerSendArrayBuffer.ets) -->

``` TypeScript
import { worker, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker('entry/ets/workers/Worker.ets');

const buffer: ArrayBuffer = new ArrayBuffer(1024 * 1024); // 1MB
workerInstance.postMessage(buffer, [buffer]);
// After the transfer, the ownership of buffer is transferred to the Worker thread, and the host thread can no longer access buffer
workerInstance.onmessage = (e: MessageEvents) => {
  workerInstance.terminate();
};
workerInstance.onerror = (err: ErrorEvent) => {
  console.error('worker err:' + err.message);
};
```

If the host thread still needs to access the ArrayBuffer while the Worker is processing it, the data can only be passed in copy transfer mode.

<!-- @[worker_send_copy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/CommunicationObjects/entry/src/main/ets/managers/WorkerSendArrayBufferWithCopy.ets) -->

``` TypeScript
import { worker, MessageEvents, ErrorEvent } from '@kit.ArkTS';

const workerInstance = new worker.ThreadWorker('entry/ets/workers/Worker.ets');

const buffer: ArrayBuffer = new ArrayBuffer(1024 * 1024); // 1MB
workerInstance.postMessage(buffer);
// Deep copy. The host thread and the Worker thread each hold 1MB of data, doubling the total memory usage.
workerInstance.onmessage = (e: MessageEvents) => {
  workerInstance.terminate();
};
workerInstance.onerror = (err: ErrorEvent) => {
  console.error('worker err:' + err.message);
};
```
