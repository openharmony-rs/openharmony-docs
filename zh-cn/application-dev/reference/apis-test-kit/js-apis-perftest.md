# @ohos.test.PerfTest

<!--Kit: Test Kit-->
<!--Subsystem: Test-->
<!--Owner: @inter515-->
<!--Designer: @inter515-->
<!--Tester: @laonie666-->
<!--Adviser: @Brilliantry_Rui-->

PerfTest提供白盒性能测试能力，供开发者在测试场景使用，支持对指定代码段或指定场景的性能数据测试，支持自动化执行测试代码段，并采集耗时、CPU、内存、时延、帧率等性能数据。

> **说明：**
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口在<!--RP1-->[自动化测试脚本](../../application-test/arkxtest-guidelines.md)<!--RP1End-->中使用。
> - 本模块接口不支持并发调用。
> - 本模块接口适用于手机、平板、PC/2in1、智慧屏、车机。


## 导入模块

```ts
import { PerfMetric, PerfTest, PerfTestStrategy, PerfMeasureResult } from '@kit.TestKit';
```

## PerfMetric

框架支持采集的性能指标。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.PerfTest

| 名称       | 值   | 说明     |
| ---------- | ---- | -------- |
| DURATION                  | 0 | 代码段执行耗时，单位：ms。  |
| CPU_LOAD                  | 1 | 应用进程CPU负载，取值为百分比。  |
| CPU_USAGE                 | 2 | 应用进程CPU使用率，取值为百分比。  |
| MEMORY_RSS                | 3 | 代码段单次执行结束时，应用进程占用物理内存（含共享库），单位：KB。  |
| MEMORY_PSS                | 4 | 代码段单次执行结束时，应用进程占用物理内存（不含共享库），单位：KB。  |
| APP_START_RESPONSE_TIME   | 5 | 应用启动的响应时延，单位：ms。  |
| APP_START_COMPLETE_TIME   | 6 | 应用启动的完成时延，单位：ms。  |
| PAGE_SWITCH_COMPLETE_TIME | 7 | 应用内页面切换的完成时延，单位：ms。  |
| LIST_SWIPE_FPS            | 8 | 应用内列表滑动的帧率，单位：fps。 |

> **说明**
>
> 1. 以上指标均用于采集指定应用进程的性能数据，非系统整机性能数据。
> 2. CPU（CPU_LOAD/CPU_USAGE）、内存（MEMORY_RSS/MEMORY_PSS）数据采集说明如下：
> - 测试过程中，代码段执行开始前和代码段执行结束后，会分别采集指定应用进程的CPU和内存数据，因此测试过程中需要保证被测应用进程一直存在。
> 3. 应用启动时延（APP_START_RESPONSE_TIME/APP_START_COMPLETE_TIME）数据采集说明如下：
> - 应用启动时延数据受系统打点上报限制，开始时间为点击事件上报时间点，响应时延结束时间为点击后系统响应首帧的上屏时间点（首帧显示在屏幕上的时间点），完成时延结束时间为应用启动后的首帧上屏时间点，与端到端用户感知时延存在差异。
> - 应用启动时延数据采集支持的场景：桌面点击应用图标启动、Dock栏点击应用图标启动、应用中心点击应用图标启动。
> - 单次测试期间，仅第一次指定应用启动的时延数据会被采集。
> 4. 页面切换时延（PAGE_SWITCH_COMPLETE_TIME）数据采集说明如下：
> - 页面切换时延计算受系统打点上报限制，开始时间为点击事件上报时间点，完成时延结束时间为页面切换后的首帧上屏时间点，与端到端用户感知时延存在差异。
> - 页面切换时延数据采集支持的场景：Router、Navigation控件内的页面切换。
> - 单次测试期间，仅指定应用内第一次页面切换的时延数据会被采集。
> 5. 列表滑动帧率（LIST_SWIPE_FPS）数据采集说明如下：
> - 列表滑动帧率：指的是在列表滑动时，屏幕每秒钟渲染更新帧的次数。
> - 列表滑动帧率数据采集支持的场景：ArkUI子系统List、Grid、scroll、waterflow滚动控件列表的滑动。
> - 单次测试期间，仅指定应用内第一次列表滑动的帧率数据会被采集。


## PerfTestStrategy

性能测试执行策略。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.PerfTest

| 名称 | 类型   | 只读 |  可选 | 说明        |
| ---- | ------ | ---- | ---- |-----------|
| metrics     | Array\<[PerfMetric](#perfmetric)>           | 否 | 否 | 被测性能指标列表。  |
| actionCode  | Callback\<Callback\<boolean>> | 否 | 否 | 测试代码段。  |
| resetCode   | Callback\<Callback\<boolean>> | 否 | 是 | 测试结束环境重置代码段。默认为空，框架运行时不执行此代码段。  |
| bundleName  | string                      | 否 | 是 | 被测应用包名。默认为""，框架运行时测试当前测试应用的性能数据。  |
| iterations  | number                      | 否 | 是 | 测试迭代执行次数，默认值为5。  |
| timeout     | number                      | 否 | 是 | 单次代码段（actionCode/resetCode）执行的超时时间，默认值为10000ms。  |

> **说明**
>
> 属性actionCode和resetCode的入参类型为回调函数"Callback\<boolean>"。在代码段中需要主动调用此回调函数，通知框架代码段执行完成，否则会导致代码段执行超时。
> 其中，回调函数的参数为boolean类型，true代表代码段执行符合预期，false代码段执行不符合预期。[代码示例](#create)。

## PerfMeasureResult

性能指标对应测量结果数据。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.PerfTest

| 名称   | 类型   | 只读 | 可选 | 说明                      |
| ------ | ------ | ---- | ---- | ------------------------- |
| metric        | [PerfMetric](#perfmetric)    | 是 | 否 | 被测性能指标。  |
| roundValues   | Array\<number> | 是 | 否 | 被测性能指标的各轮测量数据值。当数据采集失败时返回-1。  |
| maximum       | number        | 是 | 否 | 各轮测量数据最大值（剔除为-1的数据后计算）。  |
| minimum       | number        | 是 | 否 | 各轮测量数据最小值（剔除为-1的数据后计算）。  |
| average       | number        | 是 | 否 | 各轮测量数据平均值（剔除为-1的数据后计算）。  |


## PerfTest

PerfTest类为白盒性能测试框架的总入口，提供测试任务创建、测试代码段执行和数据采集、测量结果获取等能力。

### create

static create(strategy: PerfTestStrategy): PerfTest

静态方法，构造一个PerfTest对象，并返回该对象。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.PerfTest

**参数：**

| 参数名   | 类型   | 必填 | 说明                            |
| -------- | ------ | ---- | ------------------------------- |
| strategy | [PerfTestStrategy](#perfteststrategy) | 是   | 性能测试执行策略。 |

**返回值：**

| 类型 | 说明           |
| -------- | ---------------------- |
| [PerfTest](#perftest)   | 返回构造的PerfTest对象。 |

**错误码：**

以下错误码的详细介绍请参见[perftest错误码](errorcode-perftest.md)。

| 错误码ID | 错误信息               |
| -------- | ---------------------- |
| 32400001 | Initialization failed. |
| 32400002 | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| 32400003 | Parameter verification failed. |
| 32400007 | The API does not support concurrent calls. |

**示例：**

```ts
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => { // 定义测试代码段，入参类型'Callback<boolean>'，命名为finish
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true); // 调用finish回调函数，通知代码段执行结束，且执行符合预期
  }
  let resetCode = async (finish: Callback<boolean>) => {  // 定义测试结束环境重置代码段
    num = 0;
    finish(true);
  }
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode,
    resetCode: resetCode,
    timeout: 30000,
    iterations: 10,
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // 构造一个PerfTest对象，创建测试任务
}
```

### run

run(): Promise\<void>

运行性能测试，迭代执行测试代码段并采集性能数据，使用Promise回调。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.PerfTest

**返回值：**

| 类型 | 说明           |
| -------- | ---------------------- |
| Promise\<void>   | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[perftest错误码](errorcode-perftest.md)。

| 错误码ID | 错误信息               |
| -------- | ---------------------- |
| 32400002 | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| 32400004 | Failed to execute the callback. Possible causes: 1. An exception is thrown in the callback. 2. Callback execution timed out.  |
| 32400005 | Failed to collect metric data. |
| 32400007 | The API does not support concurrent calls. |

**示例：**

```ts
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => {
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true);
  }
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy);
  await perfTest.run(); // 运行性能测试
}
```

### getMeasureResult

getMeasureResult(metric: PerfMetric): PerfMeasureResult

获取指定性能指标的测量数据。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.PerfTest

**参数：**

| 参数名   | 类型   | 必填 | 说明                            |
| -------- | ------ | ---- | ------------------------------- |
| metric | [PerfMetric](#perfmetric) | 是   | 性能指标。 |

**返回值：**

| 类型 | 说明           |
| -------- | ---------------------- |
| [PerfMeasureResult](#perfmeasureresult)   | 性能指标对应测量结果数据。 |

**错误码：**

以下错误码的详细介绍请参见[perftest错误码](errorcode-perftest.md)。

| 错误码ID | 错误信息               |
| -------- | ---------------------- |
| 32400002 | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| 32400003 | Parameter verification failed. |
| 32400006 | Failed to obtain the measurement result. |
| 32400007 | The API does not support concurrent calls. |

**示例：**

```ts
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => {
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true);
  }
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy);
  await perfTest.run();
  let res = perfTest.getMeasureResult(PerfMetric.DURATION); // 获取指定性能指标的测量数据
}
```

### destroy

destroy(): void

销毁PerfTest对象。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Test.PerfTest

**错误码：**

以下错误码的详细介绍请参见[perftest错误码](errorcode-perftest.md)。

| 错误码ID | 错误信息               |
| -------- | ---------------------- |
| 32400002 | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| 32400007 | The API does not support concurrent calls. |

**示例：**

```ts
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => {
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true);
  }
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy);
  await perfTest.run();
  perfTest.destroy(); // 销毁PerfTest对象
}
```