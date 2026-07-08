# 长时任务开发指导（TaskPool） (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

长时任务是指执行时间较长，但仍可以表达为一次任务执行过程的任务。ArkTS-Sta中可使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)提供的LongTask构造长时任务，并通过taskpool.execute提交执行。

ArkTS-Sta中的LongTask由运行时调度执行，任务结束后资源会自动回收。taskpool.terminateTask为空实现，仅保留API兼容性，调用后不会实际终止LongTask。需要结束长时任务时，应通过共享标志、业务事件或任务内部条件主动返回。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 使用LongTask进行周期采集

以下示例使用LongTask模拟定期采集数据。宿主线程通过AtomicBoolean控制任务退出，任务执行过程中通过Task.sendData向宿主线程发送采集结果。

```ts
// ArkTS-Sta示例
class SensorSample {
  x: double;
  y: double;
  z: double;

  constructor(x: double, y: double, z: double) {
    this.x = x;
    this.y = y;
    this.z = z;
  }
}

function collectSensorData(running: AtomicBoolean): void {
  let index: int = 0;
  while (running.load()) {
    let sample: SensorSample = new SensorSample(index, index + 1, index + 2);
    taskpool.Task.sendData(sample);
    index++;

    // 示例中使用简单循环表示间隔控制。实际开发中可结合业务事件或定时器控制采集频率。
    if (index >= 10) {
      running.store(false);
    }
  }
}

async function startLongTask(): Promise<void> {
  let running: AtomicBoolean = new AtomicBoolean(true);
  let sensorTask: taskpool.LongTask = new taskpool.LongTask("sensorTask", collectSensorData, running);

  sensorTask.onReceiveData((sample: SensorSample): void => {
    console.info("Receive sample: " + sample.x + "," + sample.y + "," + sample.z); // Receive sample: 0,1,2（首次回调，后续递增）
  });

  await taskpool.execute(sensorTask);
  console.info("LongTask finished"); // LongTask finished
}
```

## 主动结束LongTask

LongTask应通过任务内部条件主动结束。宿主线程可以通过共享原子标志通知任务退出。

```ts
// ArkTS-Sta示例
function longWork(running: AtomicBoolean): string {
  while (running.load()) {
    // 执行业务逻辑。
  }
  return "stopped";
}

async function stopLongTaskByFlag(): Promise<void> {
  let running: AtomicBoolean = new AtomicBoolean(true);
  let longTask: taskpool.LongTask = new taskpool.LongTask(longWork, running);

  let promise: Promise<Any> = taskpool.execute(longTask);
  running.store(false);

  let result: Any = await promise;
  console.info("long task result: " + result); // long task result: stopped
}
```

## 使用约束

- LongTask只能执行一次，不支持重复执行。
- LongTask不支持添加到TaskGroup、SequenceRunner或AsyncRunner。
- LongTask不支持设置依赖关系、不支持延时执行、不支持周期执行。
- taskpool.terminateTask在ArkTS-Sta中不会实际终止任务。需要通过共享状态或业务协议让任务自行退出。
- LongTask中访问共享可变对象时，需要使用同步机制保证线程安全。

更多接口说明请参见[taskpool.LongTask](../reference/apis-arkts/arkts-sta-taskpool.md#longtask)。
