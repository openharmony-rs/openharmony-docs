---
kits: ["ArkTS / Ark Programming Language"]
description: "Provides development guidance for CPU intensive tasks: using TaskPool for image histogram processing and Worker for long-duration data analysis as examples, it demonstrates how to run high-computation tasks in child threads to avoid blocking the UI main thread and causing lag."
keywords: [CPU intensive task, image histogram processing, long-duration data analysis, TaskPool, Worker, child thread execution, avoid main thread blocking]
doctype: guide
status: active
---

# CPU Intensive Task Development (TaskPool and Worker)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:33:18.666Z pushedAt=2026-11-12T03:39:27.038Z nl=1 -->


CPU intensive tasks are those that require significant computational resources and can run for extended periods. If executed in the UI main thread, these tasks can block other events. Examples include image processing, video encoding, and data analysis.


To improve CPU utilization and enhance application responsiveness, you can use multithreaded concurrency in processing CPU intensive tasks.


When tasks do not need to occupy a background thread for a long time (exceeding 3 minutes of synchronous execution) and are independent of each other, TaskPool is recommended; otherwise, Worker is recommended.

The following sections use TaskPool for image histogram processing and Worker for long-duration data analysis as examples.


## Using TaskPool for Image Histogram Processing

1. Implement the logic of image processing.

2. Segment the data, and schedule related tasks using a task group.

   Create a [TaskGroup](../reference/apis-arkts/js-apis-taskpool.md#taskgroup10), add the corresponding tasks through [addTask()](../reference/apis-arkts/js-apis-taskpool.md#addtask10), then execute the task group through [execute()](../reference/apis-arkts/js-apis-taskpool.md#taskpoolexecute10) and specify the [HIGH](../reference/apis-arkts/js-apis-taskpool.md#priority) priority. After all tasks in the current task group are completed, the histogram processing results are returned at the same time.

3. Aggregate and process the result arrays.

<!-- @[process_image_histogram](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/CpuIntensiveTaskDevelopment.ets) --> 

``` TypeScript
import { taskpool } from '@kit.ArkTS';
// ...

@Concurrent
function imageProcessing(dataSlice: ArrayBuffer): ArrayBuffer {
  // Step 1: Specific image processing operations and other time-consuming operations
  return dataSlice;
}

async function histogramStatistic(pixelBuffer: ArrayBuffer): Promise<void> {
  // Step 2: Split into three segments for concurrent scheduling
  let number: number = pixelBuffer.byteLength / 3;
  let buffer1: ArrayBuffer = pixelBuffer.slice(0, number);
  let buffer2: ArrayBuffer = pixelBuffer.slice(number, number * 2);
  let buffer3: ArrayBuffer = pixelBuffer.slice(number * 2);

  let group: taskpool.TaskGroup = new taskpool.TaskGroup();
  group.addTask(imageProcessing, buffer1);
  group.addTask(imageProcessing, buffer2);
  group.addTask(imageProcessing, buffer3);

  await taskpool.execute(group, taskpool.Priority.HIGH).then((ret: Object) => {
    // Step 3: Aggregate and process the result array
  })
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World'

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            let buffer: ArrayBuffer = new ArrayBuffer(24);
            histogramStatistic(buffer).then(() => {
              this.message = 'success';
            }).catch((e: BusinessError) => {
              this.message = 'failed';
              console.error('histogramStatistic is failed.');
            });
            
            // ...
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```


## Using Worker for Time-Consuming Data Analysis

This example demonstrates training a simple housing price prediction model using housing data from a specific region. The model supports predicting housing prices based on input parameters like house size and number of rooms. Since the model requires long-running execution and the prediction relies on the model's previous results, Worker is the appropriate choice.

1. DevEco Studio provides a template for creating a Worker. Create a Worker thread, for example, named "MyWorker1".

   ![newWorker](figures/newWorker.png)

2. On the host thread, first call the ThreadWorker [constructor()](../reference/apis-arkts/js-apis-worker.md#constructor9) method to create a Worker object; then register the [onmessage()](../reference/apis-arkts/js-apis-worker.md#properties) callback to receive messages sent by the Worker thread; finally, call the [postMessage()](../reference/apis-arkts/js-apis-worker.md#postmessage9) method to send messages to the Worker thread.

   For example, send training and prediction messages to the Worker thread, and receive messages sent back by the Worker thread.

   <!-- @[call_worker_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/CpuIntensiveTaskDevelopment.ets) --> 
   
   ``` TypeScript
   import { worker } from '@kit.ArkTS';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   const workerInstance: worker.ThreadWorker = new worker.ThreadWorker('entry/ets/workers/MyWorker1.ets');
   
   let done = false;
   
   // Receive the result from the Worker child thread
   workerInstance.onmessage = (() => {
     console.info('MyWorker1.ets onmessage');
     if (!done) {
       // Execute prediction and pass in the prediction conditions
       workerInstance.postMessage({ 'type': 1, 'area': 80, 'room': 4 });
       done = true;
     }
   })
   
   workerInstance.onerror = (() => {
     // Receive error information from the Worker child thread
   })
   
   // Send a training message to the Worker child thread
   workerInstance.postMessage({ 'type': 0 });
   ```


3. In the MyWorker1.ets file, bind the Worker object, and the current thread is the Worker thread. In the Worker thread, register the [onmessage()](../reference/apis-arkts/js-apis-worker.md#properties-1) callback to receive messages sent by the host thread, and call the [postMessage()](../reference/apis-arkts/js-apis-worker.md#postmessage9-2) method to send messages to the host thread.

    For example, define the prediction model and training process in the Worker thread and interact with the host thread.

    <!-- @[interact_main_thread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/workers/MyWorker1.ets) -->
    
    ``` TypeScript
    import { worker, ThreadWorkerGlobalScope, MessageEvents, ErrorEvent } from '@kit.ArkTS';
    
    let workerPort: ThreadWorkerGlobalScope = worker.workerPort;
    
    // Assume the model is: price per square meter = (model.areaCoefficient * area + model.roomCoefficient * room) * model.basePrice
    class PriceModel {
      public areaCoefficient: number = 0;   // House area coefficient
      public roomCoefficient: number = 0;   // Room count coefficient
      public basePrice: number = 0;         // Base value
    }
    
    // Global model instance
    const model: PriceModel = new PriceModel();
    
    // Define the prediction function
    function predict(area: number, room: number): number {
      // Data example: 80 square meters with 4 rooms, the estimated house price is 22400 yuan per square meter
      return (model.areaCoefficient * area + model.roomCoefficient * room) * model.basePrice;
    }
    
    // Define the optimizer training process
    function optimize(): void {
      // The sample mainly demonstrates the overall process, and the training process is simplified
      model.areaCoefficient = 3;
      model.roomCoefficient = 500;
      model.basePrice = 10;
    }
    
    // onmessage logic of the Worker thread
    workerPort.onmessage = (e: MessageEvents): void => {
      // Select the operation based on the type of the transmitted data
      switch (e.data.type as number) {
        case 0:
          // Perform training
          optimize();
          // Send a training success message to the host thread after training
          workerPort.postMessage({ type: 'message', value: 'train success.' });
          break;
        case 1:
          // Execute prediction
          const output: number = predict(e.data.area as number, e.data.room as number);
          // Send the prediction result to the host thread
          workerPort.postMessage({ type: 'predict', value: output });
          break;
        default:
          workerPort.postMessage({ type: 'message', value: 'send message is invalid' });
          break;
      }
      // Destroy the thread as needed; not required in this sample
    }
    ```

4. After the task is completed, destroy the Worker thread. The Worker thread can be destroyed by the host thread or by itself.

    On the host thread, define the processing logic after the Worker thread is destroyed by calling the [onexit()](../reference/apis-arkts/js-apis-worker.md#properties) callback.

    <!-- @[after_destroy_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/CpuIntensiveTaskDevelopment.ets) -->
    
    ``` TypeScript
    // After the Worker thread is destroyed, execute the onexit callback.
    workerInstance.onexit = (): void => {
      console.info('worker thread terminate');
    }
    ```

    Method 1: In the host thread, call [terminate()](../reference/apis-arkts/js-apis-worker.md#terminate9) to destroy the Worker thread and stop it from receiving messages.

    ```ts
    // Destroy the Worker thread.
    workerInstance.terminate();
    ```

    Method 2: In the Worker thread, call [close()](../reference/apis-arkts/js-apis-worker.md#close9) to destroy the Worker thread and stop it from receiving messages.

    ```ts
    // Destroy the Worker thread.
    workerPort.close();
    ```