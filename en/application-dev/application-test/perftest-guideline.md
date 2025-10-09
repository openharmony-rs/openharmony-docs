# PerfTest User Guide

<!--Kit: Test Kit-->
<!--Subsystem: Test-->
<!--Owner: @inter515-->
<!--Designer: @inter515-->
<!--Tester: @laonie666-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

PerfTest provides white-box performance test capabilities for specified code segments during running, to measure the performance of specified application processes. The framework implements automatic tests through the multi-round iteration execution mechanism and environment reset mechanism, and collects and measures basic data such as the time consumption and CPU usage, and scenario-based performance data such as the startup latency and sliding frame rate. The performance test script that uses the PerfTest APIs must be developed based on the unit test framework.

## Implementation Principles

PerfTest provides ArkTS APIs for external systems, including performance test policy setting, performance test execution, and test result obtaining. <!--RP1-->For details, see [API Reference](../reference/apis-test-kit/js-apis-perftest.md)<!--RP1End-->.

The cross-language communication layer is responsible for converting ArkTS APIs at the upper layer and C++ APIs at the lower layer, including parameter verification, JSON serialization object processing, and exception handling. As the client of PerfTest, it provides the startup entry and function calling APIs. This layer is loaded and run by the test application. It communicates with the server through IPC to implement function calling and lifecycle management. In addition, this layer is responsible for managing the calling of ArkTS callback functions by the C++ layer.

The PerfTest server is responsible for the main function processing of the white-box performance test framework, including the following two parts:

- General framework running capabilities: manage C++ APIs and error codes, including API calling, parameter parsing, and exception handling. The PerfTest server runs as an independent process. It communicates with the client through IPC, listens to the client lifecycle, and keeps the process alive and starts or stops the process as required.

- White-box performance test capabilities: responsible for test task scheduling and performance data collection. Automatically perform performance tests on the running of test code segments, performance data collection, data processing, and data storage based on user-defined test policies. Currently, the following performance indicators can be collected: time consumption, CPU usage, memory usage, application startup latency, page switching latency, and list sliding frame rate.

## How to Develop

The following figure shows the process of performing a white-box performance test using the PerfTest APIs.

1. Define a performance test policy, including the test metric list, code segment to be tested, environment reset code segment, name of the app package to be tested, number of test iterations, and timeout interval for executing the code segment once. The white-box performance test is performed based on the policy.

2. Create a test task, configure the test policy, and prepare the test environment.

3. Start the test. Multiple rounds of tests are performed based on the number of test iterations. In each round of test, the performance data generated during the execution of the code segment to be tested is collected, and the environment reset code segment is executed to restore the environment. After the test is complete, the data is processed and saved.

4. Obtain the measured data values. The result is stored in an object. You can obtain the detailed data of each round of test and statistics such as the maximum value, minimum value, and average value.

5. Destroy the created object to release the memory.

The following describes how to collect the execution duration and CPU usage of a specified code segment.

### Defining a Test Policy

1. Define the test metric list.

    Define the list of performance metrics to be tested `metrics`. The type is `Array<PerfMetric>`. <!--RP2-->[PerfMetric](../reference/apis-test-kit/js-apis-perftest.md#perfmetric)<!--RP25End--> is the enumeration of performance metrics that can be collected by the framework.
    ```ts
    let metrics: Array<PerfMetric> = [ PerfMetric.DURATION, PerfMetric.CPU_USAGE ];
    ```

2. Define the code segment to be tested and the environment reset code segment.

    The code segment to be tested `actionCode` is a callback function of the `Callback<Callback<boolean>>` type. The framework automatically calls this callback function during the test and collects performance data. At the end of the execution, the input parameter `Callback<boolean>` function needs to be called to notify the framework that the execution is complete. Otherwise, the code segment execution times out. For example, when testing the performance of the `Utils.CalculateTest` method, you can call `finish(true)` to notify the framework that the code segment execution is complete.
    ```ts
    let actionCode: Callback<Callback<boolean>> = async (finish: Callback<boolean>) => {
        Utils.CalculateTest();
        finish(true);
    };
    ```

    In addition, the framework supports the definition of the environment reset code segment `resetCode`, which is used to reset the environment after a single test. The type and usage of `resetCode` are the same as those of `actionCode`. `resetCode` is executed after `actionCode` is executed, but application performance data is not collected during the execution.
    ```ts
    let resetCode: Callback<Callback<boolean>> = async (finish: Callback<boolean>) => {
        Utils.Reset();
        finish(true);
    };
    ```

3. Construct a test policy object.

    In addition to the attributes defined in the preceding steps, the framework also supports the definition of other test policies to help developers perform more accurate automatic performance tests. All test policies are defined and saved through the <!--RP3-->[PerfTestStrategy](../reference/apis-test-kit/js-apis-perftest.md#perfteststrategy)<!--RP3End--> object. During the performance test, data is collected based on the policy.
    ```ts
    let perfTestStrategy: PerfTestStrategy = {
        metrics: metrics,   // Defined in step 1
        actionCode: actionCode,   // Defined in step 2
        resetCode: resetCode,   // Defined in step 2
        bundleName: "com.example.test", // Bundle name of the app to be tested
        iterations: 10,  // Number of test iterations
        timeout: 20000  // Timeout interval for executing a code segment, in ms
    };
    ```

### Creating a Test Task and Starting the Test

  When using <!--RP4-->[PerfTest.create()](../reference/apis-test-kit/js-apis-perftest.md#create)<!--RP4End--> to create a test task, pass the `PerfTestStrategy` object defined above. Then, call the <!--RP5-->[PerfTest.run()](../reference/apis-test-kit/js-apis-perftest.md#run)<!--RP5End--> asynchronous API to start the test. The test automatically iteratively executes the code segment to be tested and collects performance data. Use the await syntax sugar to synchronously wait for the execution to complete before performing subsequent operations.
  ```ts
  let perfTest: PerfTest = PerfTest.create(perfTestStrategy);
  await perfTest.run();
  ```

### Obtaining the Test Result

  After the performance test is complete, call <!--RP6-->[PerfTest.getMeasureResult()](../reference/apis-test-kit/js-apis-perftest.md#getmeasureresult)<!--RP6End--> to obtain the test result of each indicator. The result is stored in the <!--RP7-->[PerfMeasureResult](../reference/apis-test-kit/js-apis-perftest.md#perfmeasureresult)<!--RP7End--> object. If the test is not complete or the indicator is not defined, an error code is thrown.
  ```ts
  let res1: PerfMeasureResult = perfTest.getMeasureResult(PerfMetric.DURATION);
  let res2: PerfMeasureResult = perfTest.getMeasureResult(PerfMetric.CPU_USAGE);
  ```

### Destroying Created Objects

  After the performance test is complete, if the `PerfTest` object is no longer needed, you can call <!--RP8-->[PerfTest.destroy()](../reference/apis-test-kit/js-apis-perftest.md#destroy)<!--RP8End--> to destroy the object to release memory.
  ```ts
  perfTest.destroy();
  ```

## Complete Sample Code

### Example of Collecting Basic Performance Data

The following uses the basic performance data of a specified logic execution in an application as an example. The application defines a method named 'Utils.CalculateTest()'. During the performance test, this method is executed to collect the execution duration and application CPU usage.

1. Add the **Utils.ets** file to the **main** > **ets** > **utils** folder and compile the custom function in the file.

    ```ts
    export class Utils {
      static num: number = 0
      public static CalculateTest() {
        for (let index = 0; index < 10000; index++) {
          Utils.num++;
        }
      }
      public static Reset() {
        Utils.num = 0
      }
    }
    ```

2. Compile the test code in the **PerfTest.test.ets** file in the **ohosTest** > **ets** > **test** folder.

    ```ts
    import { describe, it, expect, Level } from '@ohos/hypium';
    import { PerfMetric, PerfTest, PerfTestStrategy, PerfMeasureResult } from '@kit.TestKit';
    import { Utils } from '../../../main/ets/utils/Utils'

    export default function PerfTestTest() {
      describe('PerfTestTest', () => {
        it('testExample1', 0, async (done: Function) => {
          let metrics: Array<PerfMetric> = [ PerfMetric.DURATION, PerfMetric.CPU_USAGE ]; // Define the indicators to be tested.
          let actionCode: Callback<Callback<boolean>> = async (finish: Callback<boolean >) => { // Define the code segment to be tested.
            Utils.CalculateTest();
            finish(true);
          };
          let resetCode: Callback<Callback<boolean>> = async (finish: Callback<boolean >) => { // Define the code segment for environment reset.
            Utils.Reset();
            finish(true);
          };
          let perfTestStrategy: PerfTestStrategy = { // Define a test strategy.
            metrics: metrics,
            actionCode: actionCode,
            resetCode: resetCode,
            bundleName: "com.example.test", // Define the package name of the app to be tested. Replace it with the actual package name.
            iterations: 10, // Define the number of test iterations.
            timeout: 20000 // Define the timeout interval for executing the code segment at a time.
          };
          try {
            let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // Create a test task object PerfTest.
            await perfTest.run(); // Execute the test. Use await to wait for the completion of the asynchronous function.
            let res1: PerfMeasureResult = perfTest.getMeasureResult(PerfMetric.DURATION); // Obtain the test result of the duration.
            let res2: PerfMeasureResult = perfTest.getMeasureResult(PerfMetric.CPU_USAGE); // Obtain the test result of the CPU usage.
            perfTest.destroy(); // Destroy the PerfTest object.
            expect(res1.average).assertLessOrEqual(1000); // Assert the performance test result.
            expect(res2.average).assertLessOrEqual(30); // Assert the performance test result.
          } catch (error) {
            console.error(`Failed to execute perftest. Cause:${JSON.stringify(error)}`);
            expect(false).assertTrue()
          }
          done()
        })
      })
    }
    ```

### Scenario-based Performance Data Collection Example

The following uses the frame rate of scrolling in the list of an app as an example to describe how to open a specified app, use the UI test framework API to search for scrollable components of the Scroll type, perform scrolling operations, and collect the frame rate data during the scrolling.

1. Write the code of the **Index.ets** page in the **main** > **ets** > **pages** folder as the test demo.

    ```ts
    @Entry
    @Component
    struct ListPage {
      scroller: Scroller = new Scroller()
      private arr: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
      build() {
        Row() {
          Column() {
            Scroll(this.scroller) {
              Column() {
                ForEach(this.arr, (item: number) => {
                  Text(item.toString())
                    .width('90%')
                    .height('40%')
                    .fontSize(80)
                    .textAlign(TextAlign.Center)
                    .margin({ top: 10 })
                }, (item: string) => item)
              }
            }
            .width('100%')
            .height('100%')
            .scrollable(ScrollDirection.Vertical)
            .scrollBar(BarState.On)
            .scrollBarColor(Color.Gray)
          }
          .width('100%')
        }
        .height('100%')
      }
    }
    ```

2. Write the test code in the **PerfTest.test.ets** file in the **ohosTest** > **ets** > **test** folder.

    ```ts
    import { describe, it, expect, Level } from '@ohos/hypium';
    import { PerfMetric, PerfTest, PerfTestStrategy, PerfMeasureResult } from '@kit.TestKit';
    import { abilityDelegatorRegistry, Driver, ON } from '@kit.TestKit';
    import { Want } from '@kit.AbilityKit';

    const delegator: abilityDelegatorRegistry.AbilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
      export default function PerfTestTest() {
        describe('PerfTestTest', () => {
        it('testExample2',Level.LEVEL3, async (done: Function) => {
            let driver = Driver.create();
            await driver.delayMs(1000);
            const bundleName = abilityDelegatorRegistry.getArguments().bundleName;
            //Replace bundleName and abilityName with the actual bundle name and ability name of the app to be started.
            const want: Want = {
                bundleName: bundleName,
                abilityName: 'EntryAbility'
            };
            await delegator.startAbility(want); // Start the test app.
            await driver.delayMs(1000);
            let scroll = await driver.findComponent(ON.type('Scroll'));
            await driver.delayMs(1000);
            let center = await scroll.getBoundsCenter(); // Obtain the coordinates of the Scroll component.
            await driver.delayMs(1000);
            let metrics: Array<PerfMetric> = [PerfMetric.LIST_SWIPE_FPS]  // Specify the test metric to the frame rate during list scrolling.
            let actionCode = async (finish: Callback<boolean>) => { // Use uitest to scroll the list in the test code segment.
                await driver.fling({x: center.x, y: Math.floor(center.y * 3 / 2)}, {x: center.x, y: Math.floor(center.y / 2)}, 50, 20000);
                await driver.delayMs(3000);
                finish(true);
            };
            let resetCode = async (finish: Callback<boolean>) => {  // Scroll to the top of the list.
                await scroll.scrollToTop(40000);
                await driver.delayMs(1000);
                finish(true);
            };
            let perfTestStrategy: PerfTestStrategy = { // Define a test strategy.
                metrics: metrics,
                actionCode: actionCode,
                resetCode: resetCode,
                iterations: 5,  // Specify the number of test iterations.
                timeout: 50000, // Specify the timeout interval of actionCode and resetCode.
            };
            try {
                let perfTest: PerfTest = PerfTest.create(perfTestStrategy); // Create a test task object PerfTest.
                await perfTest.run(); // Execute the test. Use await to wait for the completion of the asynchronous function.
                let res: PerfMeasureResult = perfTest.getMeasureResult(PerfMetric.LIST_SWIPE_FPS); // Obtain the test result of the frame rate during list scrolling.
                perfTest.destroy(); // Destroy the PerfTest object.
                expect(res.average).assertLargerOrEqual(60);  // Assert the performance test result.
            } catch (error) {
                console.error(`Failed to execute perftest. Cause:${JSON.stringify(error)}`);
            }
            done();
          })
      })
    }
    ```

<!--Del-->
For details about the PerfTest project example, see [White-Box Performance Test Example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/Project/Test/perftest).
<!--DelEnd-->
