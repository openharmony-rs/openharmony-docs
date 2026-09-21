# PerfTestStrategy

```TypeScript
declare interface PerfTestStrategy
```

Represents the performance test strategy.

> **NOTE:** 
> 
> The input parameter type of the **actionCode** and **resetCode** attributes is **Callback\&lt;boolean&gt;**. You need to call
> this callback in the code segment to notify the framework that the code segment execution is complete. Otherwise, the
> code segment execution times out. The callback parameter is of the **Boolean** type. The value **true** indicates that
> the code segment execution meets the expectation, and **false** indicates the opposite.

**Since:** 20

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import {PerfMetric, PerfTestStrategy, PerfMeasureResult, PerfTest} from '@kit.TestKit';
```

## actionCode

```TypeScript
actionCode: Callback<Callback<boolean>>
```

Code segment to test. The input parameter is a callback function, which needs to be called in the code segment to notify the framework that the execution is complete. Otherwise, the execution will time out. For details, see the following description.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt;&gt;

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## bundleName

```TypeScript
bundleName?: string
```

Bundle name of the application to test. The format must be the same as that of **bundleName** in the application configuration file. To test the performance data of a non-current application, pass the bundle name of the target application. The default value is **""**, indicating that the framework tests the performance data of the current application.

**Type:** string

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## iterations

```TypeScript
iterations?: number
```

Number of test iterations. The value must be an integer greater than 0. The default value is **5**. An exception is thrown if the value is out of range.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## metrics

```TypeScript
metrics: Array<PerfMetric>
```

Array of performance metrics to test. If the array is empty, no performance metric data is collected.

**Type:** Array&lt;[PerfMetric](arkts-test-test-perftest-perfmetric-e.md)&gt;

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## resetCode

```TypeScript
resetCode?: Callback<Callback<boolean>>
```

Code segment for resetting the environment after the test is complete. This parameter is passed for resetting after each test when the test code segment modifies the global status (such as global variables and configurations). The default value is empty. This code segment is not executed when the framework is performing the test. The input parameter is a callback function, which needs to be called in the code segment to notify the framework that the execution is complete. Otherwise, the execution will time out. For details, see the following description.

**Type:** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt;&gt;

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.

## timeout

```TypeScript
timeout?: number
```

resetCode**) at a time. The value is an integer greater than 0, in milliseconds. The default value is **10000**. If the execution of a test code segment takes a long time, you can increase the value of this parameter to prevent timeout. If a timeout occurs, an exception is triggered and the test execution is terminated.

**Type:** number

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Test.PerfTest

**Test API:** This API is used only in automated test scripts.
