# PerfMeasureResult

Represents the measurement result data corresponding to the performance metric.

**Since:** 20

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import {PerfMetric, PerfTestStrategy, PerfMeasureResult, PerfTest} from '@kit.TestKit';
```

## average

```TypeScript
readonly average: number
```

Average value of the measurement data of each round (the value **-1** is excluded).

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## maximum

```TypeScript
readonly maximum: number
```

Maximum value of the measurement data of each round (the value **-1** is excluded).

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## metric

```TypeScript
readonly metric: PerfMetric
```

Performance metric to test.

**Type:** [PerfMetric](arkts-test-test-perftest-perfmetric-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## minimum

```TypeScript
readonly minimum: number
```

Minimum value of the measurement data of each round (the value **-1** is excluded).

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## roundValues

```TypeScript
readonly roundValues: Array<number>
```

Measurement data value of each round of the tested performance metric. The unit is the same as that of the corresponding [PerfMetric](arkts-test-test-perftest-perfmetric-e.md). If data collection fails, the value **-1** is returned.

**Type:** Array&lt;number&gt;

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.
