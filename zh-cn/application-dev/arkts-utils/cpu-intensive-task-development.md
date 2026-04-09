# CPU密集型任务开发指导 (TaskPool和Worker)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->


CPU密集型任务是指需要占用系统资源进行大量计算的任务，这类任务需要长时间运行，会阻塞线程中其他事件的处理，因此不适合在UI主线程中执行。例如图像处理、视频编码、数据分析等。


基于多线程并发机制处理CPU密集型任务可以提高CPU利用率，提升应用程序响应速度。


当任务不需要长时间（3分钟）占用后台线程，而是一个个独立的任务时，推荐使用TaskPool，反之推荐使用Worker。

接下来将分别以图像直方图处理和后台长时间模型预测任务为例进行说明。


## 使用TaskPool进行图像直方图处理

1. 实现图像处理的业务逻辑。

2. 对数据进行分段，并通过任务组发起关联任务调度。
   创建[TaskGroup](../reference/apis-arkts/js-apis-taskpool.md#taskgroup10)，通过[addTask()](../reference/apis-arkts/js-apis-taskpool.md#addtask10)添加对应的任务，然后通过[execute()](../reference/apis-arkts/js-apis-taskpool.md#taskpoolexecute10)执行任务组，并指定为[高优先级](../reference/apis-arkts/js-apis-taskpool.md#priority)。在当前任务组所有任务结束后，会将直方图处理结果同时返回。

3. 汇总处理结果数组。

<!-- @[process_image_histogram](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/CpuIntensiveTaskDevelopment.ets) -->

<!-- @[process_image_histogram](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/CpuIntensiveTaskDevelopment.ets) -->


## 使用Worker进行长时间数据分析

本文通过某地区提供的房价数据训练一个简易的房价预测模型，该模型支持通过输入房屋面积和房间数量去预测该区域的房价，模型需要长时间运行，房价预测需要使用前面的模型运行结果，因此需要使用Worker。

1. DevEco Studio提供了Worker创建的模板，创建一个Worker线程，例如命名为“MyWorker”。

   ![newWorker](figures/newWorker.png)

2. 在宿主线程中首先调用ThreadWorker的[constructor()](../reference/apis-arkts/js-apis-worker.md#constructor9)方法创建Worker对象；然后通过注册[onmessage()](../reference/apis-arkts/js-apis-worker.md#属性-1)回调接收Worker线程发送过来的消息；最后通过调用[postMessage()](../reference/apis-arkts/js-apis-worker.md#postmessage9)方法向Worker线程发送消息。
  例如，向Worker线程发送训练和预测的消息，并接收Worker线程发送回来的消息。

    <!-- @[call_worker_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/CpuIntensiveTaskDevelopment.ets) -->

    <!-- @[call_worker_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/CpuIntensiveTaskDevelopment.ets) -->

3. 在MyWorker.ets文件中绑定Worker对象，当前线程即为Worker线程。在Worker线程中通过注册[onmessage()](../reference/apis-arkts/js-apis-worker.md#属性-2)回调接收宿主线程发送的消息，并通过调用[postMessage()](../reference/apis-arkts/js-apis-worker.md#postmessage9-2)方法向宿主线程发送消息。
    例如，在Worker线程中定义预测模型及其训练过程，并与宿主线程进行信息交互。

    <!-- @[interact_main_thread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/workers/MyWorker1.ts) -->

    <!-- @[interact_main_thread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/workers/MyWorker1.ts) -->

4. 在Worker线程中完成任务后，可以执行销毁操作。销毁方式有两种：一是在宿主线程中销毁Worker线程；二是在Worker线程中主动销毁。

    在宿主线程中通过调用[onexit()](../reference/apis-arkts/js-apis-worker.md#属性-1)回调定义Worker线程销毁后的处理逻辑。

    <!-- @[after_destroy_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/CpuIntensiveTaskDevelopment.ets) -->

    <!-- @[after_destroy_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/CpuIntensiveTaskDevelopment.ets) -->

    方式一：在宿主线程中通过调用[terminate()](../reference/apis-arkts/js-apis-worker.md#terminate9)方法销毁Worker线程，并终止Worker接收消息。

    ```ts
    // Index.ets
    // 销毁Worker线程
    workerInstance.terminate();
    ```

    方式二：在Worker线程中通过调用[close()](../reference/apis-arkts/js-apis-worker.md#close9)方法主动销毁Worker线程，并终止Worker接收消息。

    ```ts
    // MyWorker.ets
    // 销毁线程
    workerPort.close();
    ```