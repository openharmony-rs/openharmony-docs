# PerfMeasureResult

性能指标对应测量结果数据。

**起始版本：** 20

**系统能力：** SystemCapability.Test.PerfTest

## average

```TypeScript
readonly average: number
```

各轮测量数据平均值（剔除为-1的数据后计算）。

**类型：** number

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

## maximum

```TypeScript
readonly maximum: number
```

各轮测量数据最大值（剔除为-1的数据后计算）。

**类型：** number

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

## metric

```TypeScript
readonly metric: PerfMetric
```

被测性能指标。

**类型：** PerfMetric

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

## minimum

```TypeScript
readonly minimum: number
```

各轮测量数据最小值（剔除为-1的数据后计算）。

**类型：** number

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

## roundValues

```TypeScript
readonly roundValues: Array<number>
```

被测性能指标的各轮测量数据值。当数据采集失败时返回-1。

**类型：** Array<number>

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.PerfTest

