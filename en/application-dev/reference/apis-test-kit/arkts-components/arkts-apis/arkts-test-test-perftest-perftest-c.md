# PerfTest

```TypeScript
declare class PerfTest
```

Represents the general entry of the white-box performance test framework. It provides capabilities such as test task creation, test code segment execution, data collection, and measurement result obtaining.

**Since:** 20

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import {PerfMetric, PerfTestStrategy, PerfMeasureResult, PerfTest} from '@kit.TestKit';
```

## create

```TypeScript
static create(strategy: PerfTestStrategy): PerfTest
```

Creates a [PerfTest](arkts-test-test-perftest-perftest-c.md) object and returns the object created. This API is a static API.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [PerfTestStrategy](arkts-test-test-perftest-perfteststrategy-i.md) | Yes | Performance test strategy. |

**Return value:**

| Type | Description |
| --- | --- |
| [PerfTest](arkts-test-test-perftest-perftest-c.md) | [PerfTest](arkts-test-test-perftest-perftest-c.md) object constructed, which can be used to execute test tasks, collect performance data, and obtain measurement results. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32400001](../errorcode-perftest.md#32400001-initialization-failed) | Initialization failed. |
| [32400002](../errorcode-perftest.md#32400002-internal-error) | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| [32400003](../errorcode-perftest.md#32400003-parameter-verification-failed) | Parameter verification failed. |
| [32400007](../errorcode-perftest.md#32400007-api-does-not-support-concurrent-calls) | The API does not support concurrent calls. @static |

**Examples**

```TypeScript
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => { // Define the test code segment. The input parameter type is Callback<boolean> and the name is finish.
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true); // Call the finish callback to notify that the code segment is executed successfully and as expected.
  };
  let resetCode = async (finish: Callback<boolean>) => { // Define the code segment for resetting the environment after the test ends.
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
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // Construct a PerfTest object and create a test task.
}
```

## destroy

```TypeScript
destroy(): void
```

Destroys the **PerfTest** object to release the resources occupied by the object. This method is used together with [create](#create) and is called after the **PerfTest** object is used. If this method is not called, resources may fail to be released. The **PerfTest** object should not be used after this API is called.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32400002](../errorcode-perftest.md#32400002-internal-error) | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| [32400007](../errorcode-perftest.md#32400007-api-does-not-support-concurrent-calls) | The API does not support concurrent calls. |

**Examples**

```TypeScript
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => {
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true); // Call the finish callback to notify that the code segment is executed successfully and as expected.
  };
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // Construct a PerfTest object and create a test task.
  await perfTest.run();
  perfTest.destroy(); // Destroy the PerfTest object.
}
```

## getMeasureResult

```TypeScript
getMeasureResult(metric: PerfMetric): PerfMeasureResult
```

Obtains the measurement data of a specified performance metric. This method must be called after [run](#run) is executed. Otherwise, valid measurement data cannot be obtained.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| metric | [PerfMetric](arkts-test-test-perftest-perfmetric-e.md) | Yes | Performance metric to query. |

**Return value:**

| Type | Description |
| --- | --- |
| [PerfMeasureResult](arkts-test-test-perftest-perfmeasureresult-i.md) | Measurement result of the specified performance metric, including the measurement data value and statistical values (maximum value, minimum value, and average value) of each round. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32400002](../errorcode-perftest.md#32400002-internal-error) | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| [32400003](../errorcode-perftest.md#32400003-parameter-verification-failed) | Parameter verification failed. |
| [32400006](../errorcode-perftest.md#32400006-failed-to-obtain-performance-data) | Failed to obtain the measurement result. |
| [32400007](../errorcode-perftest.md#32400007-api-does-not-support-concurrent-calls) | The API does not support concurrent calls. |

**Examples**

```TypeScript
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => {
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true); // Call the finish callback to notify that the code segment is executed successfully and as expected.
  };
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // Construct a PerfTest object and create a test task.
  await perfTest.run();
  let res = perfTest.getMeasureResult(PerfMetric.DURATION); // Obtain the measurement data of a specified performance metric.
}
```

## run

```TypeScript
run(): Promise<void>
```

Runs a performance test, iteratively executes test code segments based on the configured times, and collects performance data. This API uses a promise to return the result. In each iteration, the framework executes **actionCode** and **resetCode** (if configured) in sequence and collects performance data during the execution of **actionCode**. After the execution is complete, you can call [getMeasureResult](#getmeasureresult) to obtain the collected measurement result data.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32400002](../errorcode-perftest.md#32400002-internal-error) | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| [32400004](../errorcode-perftest.md#32400004-failed-to-execute-the-callback) | Failed to execute the callback. Possible causes: 1. An exception is thrown in the callback. 2. Callback execution timed out. |
| [32400005](../errorcode-perftest.md#32400005-failed-to-collect-performance-data) | Failed to collect metric data. |
| [32400007](../errorcode-perftest.md#32400007-api-does-not-support-concurrent-calls) | The API does not support concurrent calls. |

**Examples**

```TypeScript
import { PerfMetric, PerfTest, PerfTestStrategy } from '@kit.TestKit';

async function demo() {
  let metrics: Array<PerfMetric> = [PerfMetric.DURATION];
  let num = 0;
  let actionCode = async (finish: Callback<boolean>) => {
    for (let index = 0; index < 10000; index++) {
      num++;
    }
    finish(true); // Call the finish callback to notify that the code segment is executed successfully and as expected.
  };
  let perfTestStrategy: PerfTestStrategy = {
    metrics: metrics,
    actionCode: actionCode
  };
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // Construct a PerfTest object and create a test task.
  await perfTest.run(); // Run the performance test.
}
```
