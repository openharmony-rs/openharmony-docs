# PerfTest

PerfTest类为白盒性能测试框架的总入口。 提供测试任务创建、测试代码段执行和数据采集、测量结果获取等能力。 通过[create](#create)创建实例。

**起始版本：** 20

**系统能力：** SystemCapability.Test.PerfTest

## 导入模块

```TypeScript
```

## create

```TypeScript
static create(strategy: PerfTestStrategy): PerfTest
```

静态方法，构造一个PerfTest对象，并返回该对象。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [PerfTestStrategy](arkts-test-test-perftest-perfteststrategy-i.md) | 是 | 性能测试执行策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PerfTest](arkts-test-test-perftest-perftest-c.md) | 返回构造的PerfTest对象，可用于执行测试任务、采集性能数据和获取测量结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32400001](../errorcode-perftest.md#32400001-初始化失败) | Initialization failed. |
| [32400002](../errorcode-perftest.md#32400002-内部错误) | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| [32400003](../errorcode-perftest.md#32400003-参数校验失败) | Parameter verification failed. |
| [32400007](../errorcode-perftest.md#32400007-接口不支持并行调用) | The API does not support concurrent calls. @static |

**示例**

```TypeScript
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => { // 定义测试代码段，入参类型'Callback<boolean>'，命名为finish。
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true); // 调用finish回调函数，通知代码段执行结束，且执行符合预期。
  };
  let resetCode = async (finish: Callback<boolean>) => { // 定义测试结束环境重置代码段。
    num = 0;
    finish(true);
  };
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode,
    resetCode: resetCode,
    timeout: 30000,
    iterations: 10
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // 构造一个PerfTest对象，创建测试任务。
}
```

## destroy

```TypeScript
destroy(): void
```

销毁PerfTest对象，释放该对象占用的相关资源。与[create](#create)方法配对使用，在PerfTest对象使用完毕后调用， 未调用此方法可能导致资源无法释放。调用后不应再使用该PerfTest对象。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32400002](../errorcode-perftest.md#32400002-内部错误) | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| [32400007](../errorcode-perftest.md#32400007-接口不支持并行调用) | The API does not support concurrent calls. |

**示例**

```TypeScript
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => {
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true); // 调用finish回调函数，通知代码段执行结束，且执行符合预期。
  };
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // 构造一个PerfTest对象，创建测试任务。
  await perfTest.run();
  perfTest.destroy(); // 销毁PerfTest对象。
}
```

## getMeasureResult

```TypeScript
getMeasureResult(metric: PerfMetric): PerfMeasureResult
```

获取指定性能指标的测量数据。需要在run()执行完成后调用，否则无法获取到有效的测量数据。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| metric | [PerfMetric](arkts-test-test-perftest-perfmetric-e.md) | 是 | 指定要查询的性能指标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PerfMeasureResult](arkts-test-test-perftest-perfmeasureresult-i.md) | 指定性能指标对应的测量结果，包含各轮测量数据值及 统计值（最大值、最小值、平均值）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32400002](../errorcode-perftest.md#32400002-内部错误) | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| [32400003](../errorcode-perftest.md#32400003-参数校验失败) | Parameter verification failed. |
| [32400006](../errorcode-perftest.md#32400006-无法获取性能数据) | Failed to obtain the measurement result. |
| [32400007](../errorcode-perftest.md#32400007-接口不支持并行调用) | The API does not support concurrent calls. |

**示例**

```TypeScript
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => {
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true); // 调用finish回调函数，通知代码段执行结束，且执行符合预期。
  };
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // 构造一个PerfTest对象，创建测试任务。
  await perfTest.run();
  let res = perfTest.getMeasureResult(PerfMetric.DURATION); // 获取指定性能指标的测量数据。
}
```

## run

```TypeScript
run(): Promise<void>
```

运行性能测试，按配置次数迭代执行测试代码段并采集性能数据，使用Promise回调。每次迭代中，框架依次执行 actionCode和resetCode（若已配置），并在actionCode执行期间采集性能数据。执行完成后，可通过 [getMeasureResult](#getmeasureresult)获取采集到的测量结果数据。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32400002](../errorcode-perftest.md#32400002-内部错误) | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| [32400004](../errorcode-perftest.md#32400004-执行回调函数失败) | Failed to execute the callback. Possible causes: 1. An exception is thrown in the callback. 2. Callback execution timed out. |
| [32400005](../errorcode-perftest.md#32400005-采集性能数据失败) | Failed to collect metric data. |
| [32400007](../errorcode-perftest.md#32400007-接口不支持并行调用) | The API does not support concurrent calls. |

**示例**

```TypeScript
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => {
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true); // 调用finish回调函数，通知代码段执行结束，且执行符合预期。
  };
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // 构造一个PerfTest对象，创建测试任务。
  await perfTest.run(); // 运行性能测试。
}
```
