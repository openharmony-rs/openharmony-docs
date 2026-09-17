# PerfMeasureResult

性能指标对应测量结果数据。

**起始版本：** 20

**系统能力：** SystemCapability.Test.PerfTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## 导入模块

```TypeScript
import {PerfMetric, PerfTestStrategy, PerfMeasureResult, PerfTest} from '@kit.TestKit';
```

## average

```TypeScript
readonly average: number
```

各轮测量数据平均值（剔除为-1的数据后计算）。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.PerfTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## maximum

```TypeScript
readonly maximum: number
```

各轮测量数据最大值（剔除为-1的数据后计算）。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.PerfTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## metric

```TypeScript
readonly metric: PerfMetric
```

被测性能指标。

**类型：** [PerfMetric](arkts-test-test-perftest-perfmetric-e.md)

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.PerfTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## minimum

```TypeScript
readonly minimum: number
```

各轮测量数据最小值（剔除为-1的数据后计算）。

**类型：** number

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.PerfTest

**测试接口：** 此接口仅在自动化测试脚本中使用。

## roundValues

```TypeScript
readonly roundValues: Array<number>
```

被测性能指标的各轮测量数据值，单位与对应PerfMetric指标一致。当数据采集失败时返回-1。

**类型：** Array&lt;number&gt;

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Test.PerfTest

**测试接口：** 此接口仅在自动化测试脚本中使用。
