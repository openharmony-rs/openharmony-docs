# @ohos.test.PerfTest

<!--Kit: Test Kit-->
<!--Subsystem: Test-->
<!--Owner: @inter515-->
<!--Designer: @inter515-->
<!--Tester: @laonie666-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=dfdeddd048755ef82a0878ce3b1c104a522bb3dd translatedAt=2026-08-07T09:47:37.550Z pushedAt=2026-08-10T02:22:22.477Z -->

PerfTest provides white-box performance test capabilities in test scenarios. It can automatically execute tests on specified code segments or scenarios and collect performance data such as time required, CPU usage, memory usage, latency, and frame rate.

> **NOTE**
> - The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in <!--RP1-->[JsUnit](../../application-test/unittest-guidelines.md)<!--RP1End-->.
> - The APIs of this module do not support concurrent calls.
> - The APIs of this module are applicable to phones, tablets, PCs/2-in-1 devices, smart TVs, and head units.

## Modules to Import

```ts
import { PerfMetric, PerfTest, PerfTestStrategy, PerfMeasureResult } from '@kit.TestKit';
```

## PerfMetric

Represents performance metrics that can be collected by the framework.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Test.PerfTest

| Name      | Value  | Description    |
| ---------- | ---- | -------- |
| DURATION                  | 0 | Execution duration of a code segment, in milliseconds. |
| CPU_LOAD                  | 1 | CPU load of the application process, in percentage. |
| CPU_USAGE                 | 2 | CPU usage of the application process, in percentage. |
| MEMORY_RSS                | 3 | Physical memory (including the shared library) occupied by the application process when a code segment is executed, in KB. |
| MEMORY_PSS                | 4 | Physical memory (the proportionally allocated memory occupied by shared libraries) occupied by the application process when a code segment is executed, in KB. |
| APP_START_RESPONSE_TIME   | 5 | Response latency of application startup, in milliseconds. |
| APP_START_COMPLETE_TIME   | 6 | Completion latency of application startup, in milliseconds. |
| PAGE_SWITCH_COMPLETE_TIME | 7 | Completion latency of page switching in an application, in milliseconds. |
| LIST_SWIPE_FPS            | 8 | List scrolling frame rate in an application, in frames per second (fps). |

> **NOTE**
>
> 1. The preceding metrics collect performance data for a specified application process, not for the system.
> 2. Description of collecting the CPU data (**CPU_LOAD**/**CPU_USAGE**) and memory (**MEMORY_RSS**/**MEMORY_PSS**):
>    - During the test, the CPU and memory data of the specified application process is collected before and after the code segment execution. Therefore, ensure that the application process to be tested exists during the test.
> 3. Description of collecting the application startup latency data (**APP_START_RESPONSE_TIME**/**APP_START_COMPLETE_TIME**):
>    - Application startup latency data is subject to the system logging and reporting and may be different from what end users perceive. The start time is when the tap event is reported, the end time of the response latency is when the first frame is displayed on the screen after the tap, and the end time of the completion latency is when the first frame is displayed on the screen after the application is started.
>    - Application startup latency data can be collected in the following scenarios: tapping an application icon on the home screen, tapping an application icon on the dock bar, and tapping an application icon in the application center.
>    - During a test, only the first startup latency of the specified application is collected.
> 4. Description of collecting the page switching latency data (**PAGE_SWITCH_COMPLETE_TIME**):
>    - Page switching latency calculation is subject to the system logging and reporting and may be different from what end users perceive. The start time is when the tap event is reported, and the end time is when the first frame is displayed on the screen after the page switching.
>    - Page switching latency data can be collected in the **Router** and **Navigation** components.
>    - During a test, only the first page switching latency in the specified application is collected.
> 5. Description of collecting the list scrolling frame rate (**LIST_SWIPE_FPS**):
>    - **LIST_SWIPE_FPS**: The number of frames rendered and updated on the screen per second when the list is scrolled.
>    - Supported scenarios: list scrolling of the **List**, **Grid**, **Scroll**, and **WaterFlow** components in the ArkUI subsystem.
>    - During a test, only the first list scrolling frame rate in the specified application is collected.

## PerfTestStrategy

Represents the performance test strategy.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Test.PerfTest

| Name| Type  | Read-Only|  Optional| Description       |
| ---- | ------ | ---- | ---- |-----------|
| metrics     | Array\<[PerfMetric](#perfmetric)>           | No | No | Array of performance metrics to test. If the array is empty, no performance metric data is collected.  |
| actionCode  | Callback\<Callback\<boolean>> | No | No | Code segment to test. The input parameter is a callback function, which needs to be called in the code segment to notify the framework that the execution is complete. Otherwise, the execution will time out. For details, see the following description.  |
| resetCode   | Callback\<Callback\<boolean>> | No | Yes | Code segment for resetting the environment after the test is complete. This parameter is passed for resetting after each test when the test code segment modifies the global status (such as global variables and configurations). The default value is empty. This code segment is not executed when the framework is performing the test. The input parameter is a callback function, which needs to be called in the code segment to notify the framework that the execution is complete. Otherwise, the execution will time out. For details, see the following description. |
| bundleName  | string                      | No | Yes | Bundle name of the application to test. The format must be the same as that of **bundleName** in the application configuration file. To test the performance data of a non-current application, pass the bundle name of the target application. The default value is **""**, indicating that the framework tests the performance data of the current application.  |
| iterations  | number                      | No | Yes | Number of test iterations. The value must be an integer greater than 0. The default value is **5**. An exception is thrown if the value is out of range.  |
| timeout     | number                      | No | Yes | Timeout interval for executing a code segment (**actionCode**/**resetCode**) at a time. The value is an integer greater than 0, in milliseconds. The default value is **10000**. If the execution of a test code segment takes a long time, you can increase the value of this parameter to prevent timeout. If a timeout occurs, an exception is triggered and the test execution is terminated. |

> **NOTE**
>
> The input parameter type of the **actionCode** and **resetCode** attributes is **Callback\<boolean>**. You need to call this callback in the code segment to notify the framework that the code segment execution is complete. Otherwise, the code segment execution times out. The callback parameter is of the **Boolean** type. The value **true** indicates that the code segment execution meets the expectation, and **false** indicates the opposite.

## PerfMeasureResult

Represents the measurement result data corresponding to the performance metric.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Test.PerfTest

| Name  | Type  | Read-Only| Optional| Description                     |
| ------ | ------ | ---- | ---- | ------------------------- |
| metric        | [PerfMetric](#perfmetric)    | Yes| No| Performance metric to test. |
| roundValues   | Array\<number> | Yes | No | Measurement data value of each round of the tested performance metric. The unit is the same as that of the corresponding [PerfMetric](#perfmetric). If data collection fails, the value **-1** is returned.  |
| maximum       | number        | Yes| No| Maximum value of the measurement data of each round (the value **-1** is excluded). |
| minimum       | number        | Yes| No| Minimum value of the measurement data of each round (the value **-1** is excluded). |
| average       | number        | Yes| No| Average value of the measurement data of each round (the value **-1** is excluded). |

## PerfTest

Represents the general entry of the white-box performance test framework. It provides capabilities such as test task creation, test code segment execution, data collection, and measurement result obtaining. Call [PerfTest.create](#create) to create an instance.

### create

static create(strategy: PerfTestStrategy): PerfTest

Creates a **PerfTest** object and returns the object created. This API is a static API.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Test.PerfTest

**Parameters**

| Name  | Type  | Mandatory| Description                           |
| -------- | ------ | ---- | ------------------------------- |
| strategy | [PerfTestStrategy](#perfteststrategy) | Yes  | Performance test strategy.|

**Return value**

| Type| Description          |
| -------- | ---------------------- |
| [PerfTest](#perftest)   | **PerfTest** object constructed, which can be used to execute test tasks, collect performance data, and obtain measurement results. |

**Error codes**

For details about the error codes, see [PerfTest Error Codes](errorcode-perftest.md).

| ID| Error Message              |
| -------- | ---------------------- |
| 32400001 | Initialization failed. |
| 32400002 | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| 32400003 | Parameter verification failed. |
| 32400007 | The API does not support concurrent calls. |

**Example**

```ts
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

### run

run(): Promise\<void>

Runs a performance test, iteratively executes test code segments based on the configured times, and collects performance data. This API uses a promise to return the result. In each iteration, the framework executes **actionCode** and **resetCode** (if configured) in sequence and collects performance data during the execution of **actionCode**. After the execution is complete, you can call [getMeasureResult](#getmeasureresult) to obtain the collected measurement result data.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Test.PerfTest

**Return value**

| Type| Description          |
| -------- | ---------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [PerfTest Error Codes](errorcode-perftest.md).

| ID| Error Message              |
| -------- | ---------------------- |
| 32400002 | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| 32400004 | Failed to execute the callback. Possible causes: 1. An exception is thrown in the callback. 2. Callback execution timed out.  |
| 32400005 | Failed to collect metric data. |
| 32400007 | The API does not support concurrent calls. |

**Example**

```ts
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

### getMeasureResult

getMeasureResult(metric: PerfMetric): PerfMeasureResult

Obtains the measurement data of a specified performance metric. This method must be called after [run()](#run) is executed. Otherwise, valid measurement data cannot be obtained.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Test.PerfTest

**Parameters**

| Name  | Type  | Mandatory| Description                           |
| -------- | ------ | ---- | ------------------------------- |
| metric | [PerfMetric](#perfmetric) | Yes | Performance metric to query. |

**Return value**

| Type| Description          |
| -------- | ---------------------- |
| [PerfMeasureResult](#perfmeasureresult)   | Measurement result of the specified performance metric, including the measurement data value and statistical values (maximum value, minimum value, and average value) of each round. |

**Error codes**

For details about the error codes, see [PerfTest Error Codes](errorcode-perftest.md).

| ID| Error Message              |
| -------- | ---------------------- |
| 32400002 | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| 32400003 | Parameter verification failed. |
| 32400006 | Failed to obtain the measurement result. |
| 32400007 | The API does not support concurrent calls. |

**Example**

```ts
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

### destroy

destroy(): void

Destroys the **PerfTest** object to release the resources occupied by the object. This method is used together with [create](#create) and is called after the **PerfTest** object is used. If this method is not called, resources may fail to be released. The **PerfTest** object should not be used after this API is called.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Test.PerfTest

**Error codes**

For details about the error codes, see [PerfTest Error Codes](errorcode-perftest.md).

| ID| Error Message              |
| -------- | ---------------------- |
| 32400002 | Internal error. Possible causes: 1. IPC connection failed. 2. The object does not exist. |
| 32400007 | The API does not support concurrent calls. |

**Example**

```ts
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