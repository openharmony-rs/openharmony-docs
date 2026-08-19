# PerfMeasureResult

性能指标对应测量结果数据。

**起始版本：** 23

<!--Device-unnamed-declare interface PerfMeasureResult--><!--Device-unnamed-declare interface PerfMeasureResult-End-->

**系统能力：** SystemCapability.Test.PerfTest

## 导入模块

```TypeScript
import {PerfMetric, PerfTestStrategy, PerfMeasureResult, PerfTest} from '@kit.TestKit';
```

## average

```TypeScript
readonly average: double
```

各轮测量数据平均值（剔除为-1的数据后计算）。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMeasureResult-readonly average: double--><!--Device-PerfMeasureResult-readonly average: double-End-->

**系统能力：** SystemCapability.Test.PerfTest

## maximum

```TypeScript
readonly maximum: double
```

各轮测量数据最大值（剔除为-1的数据后计算）。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMeasureResult-readonly maximum: double--><!--Device-PerfMeasureResult-readonly maximum: double-End-->

**系统能力：** SystemCapability.Test.PerfTest

## metric

```TypeScript
readonly metric: PerfMetric
```

被测性能指标。

**类型：** [PerfMetric](arkts-test-test-perftest-perfmetric-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMeasureResult-readonly metric: PerfMetric--><!--Device-PerfMeasureResult-readonly metric: PerfMetric-End-->

**系统能力：** SystemCapability.Test.PerfTest

## minimum

```TypeScript
readonly minimum: double
```

各轮测量数据最小值（剔除为-1的数据后计算）。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMeasureResult-readonly minimum: double--><!--Device-PerfMeasureResult-readonly minimum: double-End-->

**系统能力：** SystemCapability.Test.PerfTest

## roundValues

```TypeScript
readonly roundValues: Array<double>
```

被测性能指标的各轮测量数据值，单位与对应PerfMetric指标一致。当数据采集失败时返回-1。

**类型：** Array&lt;double&gt;

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PerfMeasureResult-readonly roundValues: Array<double>--><!--Device-PerfMeasureResult-readonly roundValues: Array<double>-End-->

**系统能力：** SystemCapability.Test.PerfTest

