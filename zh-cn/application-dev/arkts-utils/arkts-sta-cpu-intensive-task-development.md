# CPU密集型任务开发指导（TaskPool和EAWorker） (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

CPU密集型任务是指需要占用较多CPU资源进行大量计算的任务，例如图像处理、视频编码、数据分析、模型训练和预测等。这类任务不适合在UI主线程中执行。ArkTS-Sta中，独立、短时或可拆分的CPU密集型任务推荐使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)；需要长期保留计算上下文、模型状态或固定线程语义时，推荐使用[EAWorker（独占线程任务执行器）(ArkTS)](../reference/apis-arkts/eaworker_managed.md)。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 使用TaskPool进行图像直方图处理

TaskPool适合将一批独立计算任务拆分后并发执行。以下示例将像素缓冲区分为三段，通过TaskGroup提交到TaskPool并发处理。

```ts
// ArkTS-Sta示例
function imageProcessing(dataSlice: ArrayBuffer): ArrayBuffer {
  // 执行图像处理、直方图统计等CPU密集型操作。
  return dataSlice;
}

async function histogramStatistic(pixelBuffer: ArrayBuffer): Promise<void> {
  let sliceSize: int = (pixelBuffer.byteLength / 3).toInt();
  let thirdStart: int = sliceSize * 2;
  let buffer1: ArrayBuffer = pixelBuffer.slice(0, sliceSize);
  let buffer2: ArrayBuffer = pixelBuffer.slice(sliceSize, thirdStart);
  let buffer3: ArrayBuffer = pixelBuffer.slice(thirdStart);

  let group: taskpool.TaskGroup = new taskpool.TaskGroup();
  group.addTask(imageProcessing, buffer1);
  group.addTask(imageProcessing, buffer2);
  group.addTask(imageProcessing, buffer3);

  let result: Array<Any> = await taskpool.execute(group, taskpool.Priority.HIGH);
  console.info("histogram task count: " + result.length); // histogram task count: 3
}

async function startHistogramTask(): Promise<void> {
  let buffer: ArrayBuffer = new ArrayBuffer(24);
  await histogramStatistic(buffer);
}
```

ArkTS-Sta中ArrayBuffer默认按共享语义跨线程传递。如果任务需要独立数据副本，可以在提交任务前使用slice创建新ArrayBuffer，避免任务之间修改同一段数据。

## 使用EAWorker进行长时间数据分析

当计算任务需要长时间保留模型状态，或者后续预测依赖前一次训练结果时，推荐使用EAWorker。EAWorker对应独占工作线程，可复用线程内状态。

```ts
// ArkTS-Sta示例
class PredictModel {
  private result: Array<int> = [];

  optimize(): void {
    // 执行模型训练。
    this.result = [100, 200, 300];
  }

  predict(index: int): int {
    return this.result[index];
  }
}

function trainModel(model: PredictModel): string {
  model.optimize();
  return "train success";
}

function predictModel(model: PredictModel, index: int): int {
  return model.predict(index);
}

async function runModelInEAWorker(): Promise<void> {
  let model: PredictModel = new PredictModel();
  let worker: EAWorker = new EAWorker("modelWorker");
  worker.start();

  try {
    let trainJob = await worker.run<string>(trainModel, model) as Job<string>;
    let trainResult: string = trainJob.Await();
    console.info("train result: " + trainResult); // train result: train success

    let predictJob = await worker.run<int>(predictModel, model, 0) as Job<int>;
    let predictResult: int = predictJob.Await();
    console.info("predict result: " + predictResult); // predict result: 100
  } finally {
    await worker.join();
  }
}
```

如果多个线程会同时访问模型对象，应使用锁保护模型状态，或将模型对象只在EAWorker线程中读写，通过run串行提交训练和预测任务。

## 使用建议

- 可拆分、无固定线程要求的计算任务优先使用TaskPool和TaskGroup。
- 需要固定线程上下文、长期复用模型状态或持续处理请求时使用EAWorker。
- 不要在TaskPool任务中执行无限期阻塞逻辑。
- 共享可变对象时需要显式同步；只读数据或显式拷贝后的数据更适合并行计算。
- CPU密集型任务数量较多时，应结合任务优先级和任务拆分粒度，避免过多小任务带来调度开销。
