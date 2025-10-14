# JsUnit User Guide

<!--Kit: Test Kit-->
<!--Subsystem: Test-->
<!--Owner: @inter515-->
<!--Designer: @inter515-->
<!--Tester: @laonie666-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

JsUnit is the basic foundation of the automatic test framework. It provides capabilities such as test script identification, scheduling, execution, and result summary. You can call the UI test framework and white-box performance test framework APIs in test scripts to write test cases.<br>
This document describes the main functions, implementation principles, and development procedure of the unit test framework.


## Framework Capabilities

The unit test framework is the basic foundation of the test framework. It provides capabilities such as test script identification, scheduling, execution, and result summary. The following table describes the functions of the unit test framework.
|   Feature    | Description                                                    |
|  -------- | ------------------------------------------------------------ |
|  Basic process| Allows you to write and asynchronously execute test cases.                                |
|  Assertion library  | Checks whether the actual result value of a test case is the same as the expected value.                        |
|  Mock capability| Allows you to mock functions and modify the function behavior to return a specified value or perform a specified operation.|
|  Data-driven| Provides the data-driven capability, allowing you to reuse the same test script and use different input data to drive the execution of the test script.|
| Special capability| Allows you to filter test suites and test cases, execute test cases randomly, perform pressure tests, set timeout, and set the error-triggered stop mode and skip execution mode.|

  **Figure 1 Main functions of the unit test framework**

  ![](figures/UnitTest.PNG)


## Release Mode
The unit test framework is released as an ohpm package. For details about the version information, see [Service Component Official Website](https://ohpm.openharmony.cn/#/en/detail/@ohos%2Fhypium). After downloading DevEco Studio, you can configure the version number in the devDependencies node in the [oh-package.json5](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-oh-package-json5) file of the application project to use the framework functions of the corresponding version.

**Example Configuration**
```json
"devDependencies": {
    "@ohos/hypium": "1.0.24"
  }
```

## Writing and Executing Test Scripts Based on ArkTS

### Environment Setup

Write test scripts in DevEco Studio. Download [DevEco Studio](https://developer.huawei.com/consumer/en/download/) and complete <!--RP1-->[hdc configuration](../dfx/hdc.md)<!--RP1End-->.

### Creating a Test Script

Create an ArkTS test case by referring to [DevEco Studio Guide](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-instrument-test#section36049271219).

### Write the unit test script

A complete test script must contain the following basic elements:

1. Import the dependency package to use the APIs provided by the unit test framework and the APIs that need to be used by other test scripts. For details about the modules to be imported, see the following example.
2. Write test code to write the test logic related to the test case.
3. Call the assertion API to set checkpoints in the test code to check whether the test case meets the expectation.

The following is a simple example. The test scenario is as follows: Start the page to be tested and check whether the page displayed on the device is the expected page.

```ts
import { describe, it, expect, Level } from '@ohos/hypium';
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility, Want } from '@kit.AbilityKit';

const delegator = abilityDelegatorRegistry.getAbilityDelegator();
function sleep(time: number) {
  return new Promise<void>((resolve: Function) => setTimeout(resolve, time));
}
export default function abilityTest() {
  describe('ActsAbilityTest', () =>{
    it('testExample',Level.LEVEL1, async (done: Function) => {
      console.info("unitTest: TestExample begin");
      await sleep(500);
      const bundleName = abilityDelegatorRegistry.getArguments().bundleName;
      // Start the ability to be tested.
      const want: Want = {
        bundleName: bundleName,
        abilityName: 'EntryAbility'
      }
      await delegator.startAbility(want);
      await sleep(500);
      // Obtain the ability displayed in the foreground on the device and perform assertion check.
      const ability: UIAbility = await delegator.getCurrentTopAbility();
      console.info("get top ability");
      expect(ability.context.abilityInfo.name).assertEqual('EntryAbility');
      done();
    })
  })
}
```
### Executing the Test Script in DevEco Studio

Connect to the target test device (for example, a mobile phone) and click the corresponding button on the DevEco Studio page to execute the test script. Currently, the following four modes are supported:

1. Test package level: All test cases in the test package are executed.
2. Execute all test cases in the *.ets file.
3. Execute all test cases defined in the describe API.
4. Execute a specified test case, that is, the it API.

The following shows how to execute a test file (test class). For details about other execution methods, see [Performing Local Tests in Running Mode](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-instrument-test#section1574003717165).

![](figures/Execute.PNG)

* Viewing the test result

After the test is complete, you can view the test result in DevEco Studio.

![](figures/TestResult.PNG)

* Viewing the test case coverage

After the test case is executed, you can view the test case coverage. For details, see [Performing Instrument Tests with Code Coverage](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-instrument-test#section1989615417457).

### Executing Test Scripts in the CLI

The script execution requires a connected hardware device. Developers install the test package on the connected device, run the aa test command in the CLI, and set execution parameters to trigger the execution of test cases.

* aa test Command List

The following lists the common commands used in the unit test. For details about other aa test commands and their meanings, see <!--RP2-->[Command Reference](../tools/aa-tool.md)<!--RP2End-->.

| Parameter | Description                         | Example                      |
| ------------- |  -------------------------------------- | ---------------------------------- |
| --bundleName/-b  |  Bundle name.                      | - b com.test.example               |
| --packageName/-p | Application module name, which is applicable to applications developed in the FA model.          | - p com.test.example.entry         |
| --moduleName/-m  |  Application module name, which is applicable to applications developed in the stage model.       | -m entry                           |
| -s            |  \<key, value> pair. The framework allows you to configure multiple case execution modes using the -s parameter. The following table describes the -s parameters and their meanings.| - s unittest /ets/testrunner/OpenHarmonyTestRunner |


| Parameter    | Description                                            | Example                             |
| ------------ | -----------------------------------------------------------------------------     | ----------------------------------------- |
| unittest     | OpenHarmonyTestRunner object used for case execution. The value can be OpenHarmonyTestRunner or a user-defined runner name.                 | -s unittest OpenHarmonyTestRunner        |
| class        | Execution mode, that is, the test suite or test case to be executed. The value can be describeName or describeName#itName.                  | -s class attributeTest#testAttributeIt    |
| notClass     | Execution mode, that is, the test suite or test case that does not need to be executed. The value can be describeName or describeName#itName.                    | -s notClass attributeTest#testAttributeIt |
| itName       |Execution mode, that is, the test case to be executed. It can be set to itName.                             | -s itName testAttributeIt                 |
| timeout      | Timeout interval for executing a test case. The value is a positive integer, in milliseconds. The default value is 5000.                     | -s timeout 15000                          |
| breakOnError | Whether to stop the test immediately when a test case fails. The value can be true (stop) or false (continue). The default value is false.<br> **Note**: This parameter is supported since @ohos/hypium 1.0.6.| -s breakOnError true                      |
| random | Whether to execute test cases in random order. If this parameter is set to true, test cases are executed in random order. The value can be true (set) or false (not set). The default value is false.<br> **Note**: This parameter is supported since @ohos/hypium 1.0.3. | -s random true                      |
| testType     | Type of the test case to be executed in filtering mode. The value can be function, performance, power, reliability, security, global, compatibility, user, standard, safety or resilience.| -s testType function                      |
| level        | Level of the test case to be executed in filtering mode. The value can be 0, 1, 2, 3, or 4.                                             | -s level 0                                |
| size         | Scale of the test case to be executed in filtering mode. The value can be small, medium, or large.                                       | -s size small        |
| stress       | Number of times that a test case is executed in pressure mode. After this parameter is set, the framework repeatedly executes the test case for the specified number of times. The value is a positive integer.<br> **Note**: This parameter is supported since @ohos/hypium 1.0.5.                 | -s stress 1000                            |
| skipMessage       | Whether to display the information about the skipped test suite and test case. The value can be true (skip) or false (not skip). The default value is false.<br>**Note**: This parameter is supported since @ohos/hypium 1.0.17.| -s skipMessage true                            |
| runSkipped       | Test suite and test case to be skipped. The value can be all, skipped, or describeName#itName.<br>**Note**: This parameter is supported since @ohos/hypium 1.0.17.| -s runSkipped all                            |

* Run the test scripts

> **NOTE**<br>
>
> The following parameter settings and command examples are based on the stage model.
>
> The command parameters must be based on the released version of the @ohos/hypium framework, and the test application package must integrate the version. Otherwise, the command parameters cannot be responded. For details about the configuration method, see [Release Mode](#release-mode). 


**Sample code 1**: Run all test cases.

```shell  
 hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner
```

**Sample code 2**: Run the describe test suite cases. If multiple cases are specified, separate them with commas (,).

```shell  
  hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner -s class s1,s2
```

**Sample code 3**: Run the specified cases in the specified test suite. If multiple cases are specified, separate them with commas (,).

```shell  
  hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner -s class testStop#stop_1,testStop1#stop_0
```

**Sample code 4**: Run all cases except the specified configuration. If multiple test suites are not executed, separate them with commas (,).

```shell  
  hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner -s notClass testStop
```

**Sample code 5**: Run all cases with the specified it name. If multiple cases are specified, separate them with commas (,).

```shell  
  hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner -s itName stop_0
```

**Sample code 6**: Configure the timeout interval for executing cases.

```shell  
  hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner -s timeout 15000
```

**Sample code 7**: Execute cases in the error-triggered stop mode.

```shell  
  hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner -s breakOnError true
```

**Sample code 8**: Run test cases that match the test type.

```shell  
  hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner -s testType function
```

**Example code 9**: Execute test cases that match the test level.

```shell  
  hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner -s level 0
```

**Example code 10**: Execute test cases that match the test scale.

```shell  
  hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner -s size small
```

**Example code 11**: Execute test cases for a specified number of times.

```shell  
  hdc shell aa test -b xxx -m xxx -s unittest OpenHarmonyTestRunner -s stress 1000
```

* View the test result.

1. During the command line execution, the framework prints the following log information.

 ```
  OHOS_REPORT_STATUS: class=testStop
  OHOS_REPORT_STATUS: current=1
  OHOS_REPORT_STATUS: id=JS
  OHOS_REPORT_STATUS: numtests=447
  OHOS_REPORT_STATUS: stream=
  OHOS_REPORT_STATUS: test=stop_0
  OHOS_REPORT_STATUS_CODE: 1

  OHOS_REPORT_STATUS: class=testStop
  OHOS_REPORT_STATUS: current=1
  OHOS_REPORT_STATUS: id=JS
  OHOS_REPORT_STATUS: numtests=447
  OHOS_REPORT_STATUS: stream=
  OHOS_REPORT_STATUS: test=stop_0
  OHOS_REPORT_STATUS_CODE: 0
  OHOS_REPORT_STATUS: consuming=4
 ```

| Log Field              | Description      |
| -------           | -------------------------|
| OHOS_REPORT_SUM    | Total number of test cases in the test suite that is being executed.|
| OHOS_REPORT_STATUS: class | Name of the test suite to which the test case belongs.|
| OHOS_REPORT_STATUS: id | The default language is JavaScript. |
| OHOS_REPORT_STATUS: numtests | Total number of test cases in the current test package.|
| OHOS_REPORT_STATUS: stream | Error information of the current test case.|
| OHOS_REPORT_STATUS: test| Name of the current test case.|
| OHOS_REPORT_STATUS_CODE | Execution result of the current test case. **0**: pass.<br>**1**: error.<br>**2**: fail.|
| OHOS_REPORT_STATUS: consuming | Time spent in executing the current test case, in milliseconds.|

2. After the command is executed, the framework prints the following log information.

 ```
  OHOS_REPORT_RESULT: stream=Tests run: 447, Failure: 0, Error: 1, Pass: 201, Ignore: 245
  OHOS_REPORT_CODE: 0

  OHOS_REPORT_RESULT: breakOnError model, Stopping whole test suite if one specific test case failed or error
  OHOS_REPORT_STATUS: taskconsuming=16029

 ```

| Log Field              | Description          |
| ------------------| -------------------------|
| run    | Total number of test cases in the current test package.|
| Failure | Number of test cases that fail to be executed.|
| Error | Number of test cases that fail to be executed. |
| Pass | Number of test cases that are successfully executed.|
| Ignore | Number of test cases that are not executed.|
| taskconsuming| Total time spent in executing the current test case, in milliseconds.|

> **NOTE**
>
> When the execution is stopped upon an error, pay attention to the Ignore field and the error message when the execution is interrupted.

## Usage of the Unit Test Framework
### Basic Process Capabilities
The unit test framework provides basic process APIs required for executing test scripts. Developers need to implement the APIs. The framework identifies test cases, schedules and executes test cases, and summarizes test results through the basic process APIs. The following table lists the basic process APIs supported by the framework.
| Name              | Description                                                                  |
| ----------------- |------------------------------------------------------------------------|
|  describe          | Defines a test suite. Multiple test case functions can be defined in a test suite, but asynchronous functions are not supported.                     |
|  it          | Defines a test case.         |
|  beforeAll         | Defines a prerequisite in a test suite. The prerequisite is executed only once before all test cases are executed.                       |
|  beforeEach        | Defines a preset condition in the test suite. The test condition is executed before each test case starts. The number of execution times is the same as the number of test cases defined by it.         |
|  afterEach         | Defines a unit cleanup condition in the test suite. The test condition is executed after each test case ends. The number of execution times is the same as the number of test cases defined by it.         |
|  afterAll          | Defines a cleanup condition in the test suite. The test condition is executed only once after all test cases end.                       |
|  beforeItSpecified | Defines a unit preset condition in the test suite. The test condition is executed only before the specified test case starts.<br>**Note**: This function is supported since @ohos/hypium 1.0.15.|
|  afterItSpecified  | Defines a unit cleanup condition in the test suite. The test condition is executed only after the specified test case ends.<br>**Note**: This function is supported since @ohos/hypium 1.0.15.|
|  expect            | Supports multiple assertion capabilities such as bool type judgment.                       |
|  xdescribe    | Defines a skipped test suite. Multiple test case functions can be defined in the test suite, but asynchronous functions are not supported.<br>**Note**: This function is supported since @ohos/hypium 1.0.17.                            |
|  xit                | Defines a skipped test case.<br>**Note**: This function is supported since @ohos/hypium 1.0.17.                    |


**Sample code 1**: beforeAll/beforeEach/afterEach/afterAll usage example

```ts
import { describe, beforeAll, beforeEach, afterEach, afterAll, it, expect, Level } from '@ohos/hypium';

export default function exampleTest() {
  
  describe('ExampleTest', () =>{
    let testNumA : number = 1;
    let testNumB : number = 1;
    
    beforeAll(() => {
      testNumA++;
    })
  
    beforeEach(() => {
      testNumA++;
      testNumB++;
    })
 
    afterEach(() => {
      testNumA++;
    })
  
    afterAll(() => {
      expect(testNumA).assertEqual(5);
    })
     
    it('testExampleA',Level.LEVEL1, async (done: Function) => {
      console.info("unitTest: testExampleA begin");
      expect(testNumA).assertEqual(3);
      expect(testNumB).assertEqual(2);
      done();
    })

    it('testExampleB',Level.LEVEL1, async (done: Function) => {
      console.info("unitTest: testExampleB begin");
      expect(testNumA).assertEqual(5);
      expect(testNumB).assertEqual(3);
      done();
    })
  })
}
```
**Example 2**: beforeItSpecified/afterItSpecified (supported since 1.0.15)
```ts
import { describe, beforeItSpecified, afterItSpecified, it, expect, Level } from '@ohos/hypium';

export default function exampleTest() {
    
  describe('ExampleTest', () =>{
   let testNumA : number = 1;
   let testNumB : number = 1;

   beforeItSpecified(['testExampleB'], () => {
      testNumB++;
    })
   afterItSpecified(['testExampleA'], () => {
      testNumA++;
    })
      
    it('testExampleA',Level.LEVEL1, async (done: Function) => {
      console.info("unitTest: testExampleA begin");
      expect(testNumA).assertEqual(1);
      expect(testNumB).assertEqual(1);
      done();
    })

    it('testExampleB',Level.LEVEL1, async (done: Function) => {
      console.info("unitTest: testExampleB begin");
      expect(testNumA).assertEqual(2);
      expect(testNumB).assertEqual(2);
      done();
    })
  })
}
```
**Example code 3**: xit usage example, supported since version 1.0.17

```ts
import { describe, xit, it, Level } from '@ohos/hypium';

export default function describeExampleTest() {
  
  describe('ExampleTest', () =>{
    xit('testExampleA',Level.LEVEL1, async (done: Function) => {
      console.info("unitTest: testExampleA begin");
      done();
    })

    it('testExampleB',Level.LEVEL1, async (done: Function) => {
      console.info("unitTest: testExampleB begin");
      done();
    })
  })
}
```

### Assertions
The unit test framework provides various assertion APIs for developers to use in different test scenarios. For details about the APIs, see the following table.
| Name               | Description                                                       |
| :------------------|-------------------------------------------------------------|
|  assertClose        | Checks whether the difference between the actual value and the expected value is within the specified error range.        |
|  assertContain      | Checks whether the actual value contains the expected value.                             |
|  assertEqual        | Checks whether the actual value is equal to the expected value.                           |
|  assertFail         | Throws an error.                                                    |
|  assertFalse        | Checks whether the actual value is false.                                     |
|  assertTrue         | Checks whether the actual value is true.                                      |
|  assertInstanceOf   | Checks whether the actual value is of the expected type. Basic types are supported.                      |
|  assertLarger       | Checks whether the actual value is greater than the expected value.                              |
|  assertLargerOrEqual       | Checks whether the actual value is greater than or equal to the expected value.                            |
|  assertLess         | Checks whether the actual value is less than the expected value.                              |
|  assertLessOrEqual         | Checks whether the actual value is less than or equal to the expected value.                            |
|  assertNull         | Checks whether the actual value is null.                                      |
|  assertThrowError   | Checks whether the error content of the actual value is the expected exception type.                     |
|  assertUndefined    | Checks whether the actual value is undefined.                                 |
|  assertNaN          |  Checks whether the actual value is NaN.<br> **Note**: This function is supported since @ohos/hypium 1.0.4.                     |
|  assertNegUnlimited | Checks whether the actual value is equal to Number.NEGATIVE_INFINITY.<br> **Note**: This function is supported since @ohos/hypium 1.0.4.   |
|  assertPosUnlimited | Checks whether the actual value is equal to Number.POSITIVE_INFINITY.<br> **Note**: This function is supported since @ohos/hypium 1.0.4.    |
|  assertDeepEquals   | Checks whether the actual value is equal to the expected value.<br> **Note**: This function is supported since @ohos/hypium 1.0.4.              |
|  assertPromiseIsPending | Checks whether the promise is in the pending state.<br>**Note**: This function is supported since @ohos/hypium 1.0.4.                        |
|  assertPromiseIsRejected | Checks whether the promise is in the rejected state.<br>**Note**: This function is supported since @ohos/hypium 1.0.4.                       |
|  assertPromiseIsRejectedWith | Checks whether the promise is in the rejected state and compares the execution result.<br>**Note**: This function is supported since @ohos/hypium 1.0.4.            |
|  assertPromiseIsRejectedWithError |  Checks whether the promise is in the rejected state, contains an exception, and compares the exception type and exception information.<br>**Note**: This function is supported since @ohos/hypium 1.0.4.|
|  assertPromiseIsResolved | Checks whether the promise is in the resolved state.<br>**Note**: This function is supported since @ohos/hypium 1.0.4.                       |
|  assertPromiseIsResolvedWith |Checks whether the promise is in the resolved state and compares the result value.<br> **Note**: This function is supported since @ohos/hypium 1.0.4.           |
|  not                | Asserts the negation of all the preceding assertions.<br>**Description**: This method is supported since @ohos/hypium 1.0.4.          |

**Sample Code**
```ts
import { describe, it, expect, Level } from '@ohos/hypium';

export default function exampleTest() {
  describe('ExampleTest', () =>{
    it('assertCloseTest', Level.LEVEL1, () => {
      let a: number = 100;
      let b: number = 0.1;
      expect(a).assertClose(99, b);
    })

    it('assertContain_1', Level.LEVEL1, () => {
      let a = "abc";
      expect(a).assertContain('b');
    })

    it('assertContain_2', Level.LEVEL1, () => {
      let a = [1, 2, 3];
      expect(a).assertContain(1);
    })

    it('assertEqualTest', Level.LEVEL1, () => {
      expect(3).assertEqual(3);
    })

    it('assertFailTest', Level.LEVEL1, () => {
      expect().assertFail(); // The test case fails.
    })

    it('assertFalseTest', Level.LEVEL1, () => {
      expect(false).assertFalse();
    })

    it('assertTrueTest', Level.LEVEL1, () => {
      expect(true).assertTrue();
    })

    it('assertInstanceOfTest', Level.LEVEL1, () => {
      let a: string = 'strTest';
      expect(a).assertInstanceOf('String');
    })

    it('assertLargerTest', Level.LEVEL1, () => {
      expect(3).assertLarger(2);
    })

    it('assertLessTest', Level.LEVEL1, () => {
      expect(2).assertLess(3);
    })

    it('assertNullTest', Level.LEVEL1, () => {
      expect(null).assertNull();
    })

    it('assertThrowErrorTest', Level.LEVEL1, () => {
      expect(() => {
        throw new Error('test');
      }).assertThrowError('test');
    })

    it('assertUndefinedTest', Level.LEVEL1, () => {
      expect(undefined).assertUndefined();
    })

    it('assertLargerOrEqualTest', Level.LEVEL1, () => {
      expect(3).assertLargerOrEqual(3);
    })

    it('assertLessOrEqualTest', Level.LEVEL1, () => {
      expect(3).assertLessOrEqual(3);
    })

    it('assertNaNTest', Level.LEVEL1, () => {
      expect(Number.NaN).assertNaN(); // true
    })

    it('assertNegUnlimitedTest', Level.LEVEL1, () => {
      expect(Number.NEGATIVE_INFINITY).assertNegUnlimited(); // true
    })

    it('assertPosUnlimitedTest', Level.LEVEL1, () => {
      expect(Number.POSITIVE_INFINITY).assertPosUnlimited(); // true
    })

    it('deepEquals_null_true', Level.LEVEL1, () => {
      expect(null).assertDeepEquals(null);
    })

    it('deepEquals_array_not_have_true', Level.LEVEL1, () => {
      const a: Array<number> = [];
      const b: Array<number> = [];
      expect(a).assertDeepEquals(b);
    })

    it('deepEquals_map_equal_length_success', Level.LEVEL1, () => {
      const a: Map<number, number> = new Map();
      const b: Map<number, number> = new Map();
      a.set(1, 100);
      a.set(2, 200);
      b.set(1, 100);
      b.set(2, 200);
      expect(a).assertDeepEquals(b);
    })

    it("deepEquals_obj_success_1", Level.LEVEL1, () => {
      const a: SampleTest = {x: 1};
      const b: SampleTest = {x: 1};
      expect(a).assertDeepEquals(b);
    })

    it("deepEquals_regExp_success_0", Level.LEVEL1, () => {
      const a: RegExp = new RegExp("/test/");
      const b: RegExp = new RegExp("/test/");
      expect(a).assertDeepEquals(b);
    })

    it('assertPromiseIsPendingTest', Level.LEVEL1, async () => {
      let p: Promise<void> = new Promise<void>(() => {});
      await expect(p).assertPromiseIsPending();
    })

    it('assertPromiseIsRejectedTest', Level.LEVEL1, async () => {
      let info: PromiseInfo = {res: "no"};
      let p: Promise<PromiseInfo> = Promise.reject(info);
      await expect(p).assertPromiseIsRejected();
    })

    it('assertPromiseIsRejectedWithTest', Level.LEVEL1, async () => {
      let info: PromiseInfo = {res: "reject value"};
      let p: Promise<PromiseInfo> = Promise.reject(info);
      await expect(p).assertPromiseIsRejectedWith(info);
    })

    it('assertPromiseIsRejectedWithErrorTest', Level.LEVEL1, async () => {
      let p1: Promise<TypeError> = Promise.reject(new TypeError('number'));
      await expect(p1).assertPromiseIsRejectedWithError(TypeError);
    })
    
    it('assertPromiseIsResolvedTest', Level.LEVEL1, async () => {
      let info: PromiseInfo = {res: "result value"};
      let p: Promise<PromiseInfo> = Promise.resolve(info);
      await expect(p).assertPromiseIsResolved();
    })

    it('assertPromiseIsResolvedWithTest', Level.LEVEL1, async () => {
      let info: PromiseInfo = {res: "result value"};
      let p: Promise<PromiseInfo> = Promise.resolve(info);
      await expect(p).assertPromiseIsResolvedWith(info);
    })

    it("test_message", Level.LEVEL1, () => {
      expect(1).message('1 is not equal 2!').assertEqual(2); // fail
    })
  })
}

interface SampleTest {
  x: number;
}

interface PromiseInfo {
  res: string;
}
```
### Mock
From @ohos/hypium 1.0.1, the unit test framework supports the mock capability. For details about the configuration method, see [Release Mode](#release-mode).

> **NOTE**
>
>Only custom objects in the application project can be mocked. System API objects cannot be mocked. For details about how to mock system APIs, see [System Module Mock Guide](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-test-mock#section8353132513310).
>
>Private functions of mock objects are not supported.

**Basic**

Mockit is a basic class for mocking. It is used to specify the instances and functions to be mocked.
| Name| Description                |
| --- |-------------------------------------------------------------------------------------------------------------------------------------------------|
| mockFunc| Mocks a function in a class instance. Asynchronous functions are supported.                                                |
| verify | Verifies whether the execution behavior of a function under the corresponding parameter meets the expectation. A VerificationMode class is returned.|
| ignoreMock | Restores the mocked function in an instance. This method is valid for mocked functions.                                                                                                  |
| clear | Restores the data mocker instance after the test case is executed. (After the restoration, the object is restored to the function before being mocked.)                                                                      |
| clearAll | Clears data and memory after the test case is executed. The mocked function in the instance is not restored.                                 |  

**VerificationMode**

VerificationMode is used to verify the number of times that a mocked function is called. It must be used together with the verify function.
| Name| Description                                                                                                                                        |
| --- |-------------------------------------------------------------------------------------------------------------------------------------------------|
| times | Verifies that the number of times that a function is called meets the expectation.                                                                                                                                 |
| once | Verifies that a function is called once.                                                                                                                                     |
| atLeast | Verifies that the minimum number of times that a function is called meets the expectation.                                                                                                                               |
| atMost | Verifies that the maximum number of times that a function is called meets the expectation.                                                                                                                              |
| never | Verifies that a function is never called.                                                                                                                               |

**when**

when is a function used to set the expected value of a function to be mocked.
| Name| Description                                                                                                                                           |
| --- |-------------------------------------------------------------------------------------------------------------------------------------------------|
| when | Checks the input function to check whether it has been mocked and marked. A built-in function is returned. After the function is executed, a class is returned to set the mock value.                                                                                                          |

After using the when function, you need to use the following functions to set the return value of the function after mocking.
| Name| Description                                                                                                                                           |
| --- |-------------------------------------------------------------------------------------------------------------------------------------------------|
| afterReturn | Sets a custom expected return value, for example, a character string or a promise.                                                                                                         |
| afterReturnNothing| Sets the expected return value to undefined.                                                                                                                         |
| afterAction | Sets the expected return value to be an action executed by a function.                                                                                                                               |
| afterThrow | Sets the expected return value to an exception and specifies the exception description.                                                                                                                             |

**ArgumentMatchers APIs**

ArgumentMatchers is used to customize function parameters. You can use ArgumentMatchers to set expected return values based on certain rules. ArgumentMatchers provides enumerated values or functions for developers.
| Enumeration Name| Description                          |
| --- |-------------------------------------------------------------------------------------------------------------------------------------------------|
| any | Sets the expected return value for any parameter (except undefined and null) passed by the user. ArgumentMatchers.any is used.                                                                          |
| anyString | Returns the expected value if a string is passed in. This API must be called by **ArgumentMatchers.anyString**.                                                                                     |
| anyBoolean | Returns the expected value if a Boolean value is passed in. This API must be called by **ArgumentMatchers.anyBoolean**.                                                                              |
| anyFunction | Returns the expected value if a function is passed in. This API must be called by **ArgumentMatchers.anyFunction**.                                                                            |
| anyNumber | Returns the expected value if a number is passed in. This API must be called by **ArgumentMatchers.anyNumber**.                                                                                    |
| anyObj | Returns the expected value if an object is passed in. This API must be called by **ArgumentMatchers.anyObj**.           |

| Name | Description    |
| --- |--------------|                                           
| matchRegexs | Sets the expected return value for any parameter that meets the regular expression verification passed by the user. ArgumentMatchers.matchRegexs(Regex) is used.     |


> **NOTE**
>To use the mock capability, you must import the MockKit module. You can import the when module based on the site requirements.
>
>Example: import {describe, expect, it, MockKit, when} from '@ohos/hypium'

**Example code 1**: Using afterReturn/afterReturnNothing to set the expected return value

```ts
import { describe, expect, it, MockKit, when } from '@ohos/hypium';

class ClassName {
  constructor() {
  }

  method_1(arg: string) {
    return '888888';
  }

  method_2(arg: string) {
    return '999999';
  }
}
export default function afterReturnTest() {
  describe('afterReturnTest', () => {
    it('afterReturnTest', 0, () => {
      console.info("it1 begin");
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Initialize the ClassName object claser.
      let claser: ClassName = new ClassName();
      // Perform the mock operation on the method_1 function of the ClassName class.
      let mockfunc: Function = mocker.mockFunc(claser, claser.method_1);
      // After the claser.method_1 function is mocked, the function returns 1 when 'testA' is used as the input parameter and returns undefined when 'testB' is used as the input parameter.
      when(mockfunc)('testA').afterReturn('1');
      when(mockfunc)('testB').afterReturnNothing();
      // Assert the mocked function to check whether the function returns the expected result 1 when 'testA' is used as the input parameter and returns undefined when 'testB' is used as the input parameter.
      expect(claser.method_1('testA')).assertEqual('1'); // The assertion is successful.
      expect(claser.method_1('testB')).assertUndefined(); // The assertion is successful.
    })
  })
}
```

**Example code 2**: Use ArgumentMatchers to set the parameter type to any (excluding undefined and null).

```ts
import { describe, expect, it, MockKit, when, ArgumentMatchers } from '@ohos/hypium';

class ClassName {
  constructor() {
  }

  method_1(arg: string) {
    return '888888';
  }

  method_2(arg: string) {
    return '999999';
  }
}
export default function argumentMatchersAnyTest() {
  describe('argumentMatchersAnyTest', () => {
    it('testMockfunc', 0, () => {
      console.info("it1 begin");
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Initialize the ClassName object claser.
      let claser: ClassName = new ClassName();
      // Perform the mock operation on the method_1 function of the ClassName class.
      let mockfunc: Function = mocker.mockFunc(claser, claser.method_1);
      // After the claser.method_1 function is mocked, the function returns 1 when being called regardless of the parameter type.
      when(mockfunc)(ArgumentMatchers.any).afterReturn('1');
      // Pass different parameters to check whether the expected result is returned.
      expect(claser.method_1('test')).assertEqual('1'); // The assertion is successful.
      expect(claser.method_1("123")).assertEqual('1');// The assertion is successful.
      expect(claser.method_1("true")).assertEqual('1');// The assertion is successful.
    })
  })
}
```

**Example code 3**: Use ArgumentMatchers to set the parameter type to String.

```ts
import { describe, expect, it, MockKit, when, ArgumentMatchers } from '@ohos/hypium';

class ClassName {
  constructor() {
  }

  method_1(arg: string) {
    return '888888';
  }

  method_2(arg: string) {
    return '999999';
  }
}
export default function argumentMatchersTest() {
  describe('argumentMatchersTest', () => {
    it('testMockfunc', 0, () => {
      console.info("it1 begin");
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Initialize the ClassName object claser.
      let claser: ClassName = new ClassName();
      // Mock the method_1 function of the ClassName class.
      let mockfunc: Function = mocker.mockFunc(claser, claser.method_1);
      // Expect that after the claser.method_1 function is mocked, the function returns 1 when being called with any string type as the parameter.
      when(mockfunc)(ArgumentMatchers.anyString).afterReturn('1');
      // Pass parameters of different string types and check whether the result meets the expectation.
      expect(claser.method_1('test')).assertEqual('1'); // The assertion is successful.
      expect(claser.method_1('abc')).assertEqual('1'); // The assertion is successful.
    })
  })
}
```

**Example code 4**: Use ArgumentMatchers to set the parameter type to matchRegexs (Regex), that is, regular expression.

```ts
import { describe, expect, it, MockKit, when, ArgumentMatchers } from '@ohos/hypium';

class ClassName {
  constructor() {
  }

  method_1(arg: string) {
    return '888888';
  }

  method_2(arg: string) {
    return '999999';
  }
}
export default function matchRegexsTest() {
  describe('matchRegexsTest', () => {
    it('testMockfunc', 0, () => {
      console.info("it1 begin");
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Initialize the ClassName object claser.
      let claser: ClassName = new ClassName();
      // Perform the mock operation on the method_1 function of the ClassName class.
      let mockfunc: Function = mocker.mockFunc(claser, claser.method_1);
      // Expect that the claser.method_1 function returns 1 when the input parameter is test.
      when(mockfunc)(ArgumentMatchers.matchRegexs(new RegExp("test"))).afterReturn('1');
      // Verify whether the input parameter test meets the expectation.
      expect(claser.method_1('test')).assertEqual('1'); // The assertion is successful.
    })
  })
}
```

**Example code 5**: Use the verify function to verify whether the execution behavior of the mocked function is as expected.

```ts
import { describe, it, MockKit } from '@ohos/hypium';

class ClassName {
  constructor() {
  }

  method_1(...arg: string[]) {
    return '888888';
  }

  method_2(...arg: string[]) {
    return '999999';
  }
}
export default function verifyTest() {
  describe('verifyTest', () => {
    it('testMockfunc', 0, () => {
      console.info("it1 begin");
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Initialize the ClassName object claser.
      let claser: ClassName = new ClassName();
      // Perform the mock operation on method_1 and method_2 of the ClassName class.
      mocker.mockFunc(claser, claser.method_1);
      mocker.mockFunc(claser, claser.method_2);
      // Call the functions.
      claser.method_1('abc', 'ppp');
      claser.method_1('abc');
      claser.method_1('xyz');
      claser.method_1();
      claser.method_1('abc', 'xxx', 'yyy');
      claser.method_1();
      claser.method_2('111');
      claser.method_2('111', '222');
      // Verify the two functions after mock. Verify method_2. Verify that method_2 has been executed once when the parameter is only 111.
      mocker.verify('method_2',['111']).once(); // The assertion is successful.
    })
  })
}
```

**Example code 6**: Use the ignoreMock function to restore the implementation of the specified mocked function.

```ts
import { describe, expect, it, MockKit, when, ArgumentMatchers } from '@ohos/hypium';

class ClassName {
  constructor() {
  }

  method_1(...arg: number[]) {
    return '888888';
  }

  method_2(...arg: number[]) {
    return '999999';
  }
}
export default function ignoreMockTest() {
  describe('ignoreMockTest', () => {
    it('testMockfunc', 0, () => {
      console.info("it1 begin");
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Initialize the ClassName object claser.
      let claser: ClassName = new ClassName();
      // Mock method_1 and method_2 of the ClassName class.
      let func_1: Function = mocker.mockFunc(claser, claser.method_1);
      let func_2: Function = mocker.mockFunc(claser, claser.method_2);
      // Expect that the claser.method_1 function returns 4 after being mocked and the input parameter is of the number type.
      when(func_1)(ArgumentMatchers.anyNumber).afterReturn('4');
      // Expect that the claser.method_2 function returns 5 after being mocked and the input parameter is of the number type.
      when(func_2)(ArgumentMatchers.anyNumber).afterReturn('5');
      // Call the functions.
      expect(claser.method_1(123)).assertEqual("4");
      expect(claser.method_2(456)).assertEqual("5");
      // Restore method_1 of the two functions.
      mocker.ignoreMock(claser, claser.method_1);
      // Call the claser.method_1 function.
      expect(claser.method_1(123)).assertEqual('888888');// The assertion is successful.
    })
  })
}
```

**Example code 7**: Use the clear function to restore the original implementation of all mocked functions in the class.

```ts
import { describe, expect, it, MockKit, when, ArgumentMatchers } from '@ohos/hypium';

class ClassName {
  constructor() {
  }

  method_1(...arg: number[]) {
    return '888888';
  }

  method_2(...arg: number[]) {
    return '999999';
  }
}
export default function clearTest() {
  describe('clearTest', () => {
    it('testMockfunc', 0, () => {
      console.info("it1 begin");
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Initialize the ClassName object claser.
      let claser: ClassName = new ClassName();
      // Mock method_1 and method_2 of the ClassName class.
      let func_1: Function = mocker.mockFunc(claser, claser.method_1);
      let func_2: Function = mocker.mockFunc(claser, claser.method_2);
      // After the claser.method_1 function is mocked, the function returns 4 when being called with any number type as the parameter.
      when(func_1)(ArgumentMatchers.anyNumber).afterReturn('4');
      // After the claser.method_2 function is mocked, the function returns 5 when being called with any number type as the parameter.
      when(func_2)(ArgumentMatchers.anyNumber).afterReturn('5');
      // Call the function.
      expect(claser.method_1(123)).assertEqual('4');
      expect(claser.method_2(123)).assertEqual('5');
      // Restore all mock capabilities of the object.
      mocker.clear(claser);
      // Call the claser.method_1,claser.method_2 function and test the result.
      expect(claser.method_1(123)).assertEqual('888888');// The assertion is successful.
      expect(claser.method_2(123)).assertEqual('999999');// Assertion Execution Passed
    })
  })
}
```

**Example code 8**: Using the afterThrow function to throw a specified exception

```ts
import { describe, expect, it, MockKit, when } from '@ohos/hypium';

class ClassName {
  constructor() {
  }

  method_1(arg: string) {
    return '888888';
  }
}
export default function afterThrowTest() {
  describe('afterThrowTest', () => {
    it('testMockfunc', 0, () => {
      console.info("it1 begin");
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Initialize the ClassName object claser.
      let claser: ClassName = new ClassName();
      // Perform the mock operation on the method_1 function of the ClassName class.
      let mockfunc: Function = mocker.mockFunc(claser, claser.method_1);
      // Expect that after the claser.method_1 function is mocked, the error xxx exception is thrown when the function is called with test as the parameter.
      when(mockfunc)('test').afterThrow('error xxx');
      // Execute the function after the mock, capture the exception, and use assertEqual to check whether msg meets the expectation.
      try {
        claser.method_1('test');
      } catch (e) {
        expect(e).assertEqual('error xxx'); // Assertion execution passed
      }
    })
  })
}
```

**Example code 9**: Mocking an asynchronous return Promise object

```ts
import { describe, expect, it, MockKit, when } from '@ohos/hypium';

class ClassName {
  constructor() {
  }

  async method_1(arg: string) {
    return new Promise<string>((resolve: Function, reject: Function) => {
      setTimeout(() => {
        console.log('Execute');
        resolve('Data transfer');
      }, 2000);
    });
  }
}
export default function mockPromiseTest() {
  describe('mockPromiseTest', () => {
    it('testMockfunc', 0, async (done: Function) => {
      console.info("it1 begin");
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Initialize the ClassName object claser.
      let claser: ClassName = new ClassName();
      // Perform the Mock operation on the method_1 function of the ClassName class.
      let mockfunc: Function = mocker.mockFunc(claser, claser.method_1);
      // Expect that after the claser.method_1 function is mocked, a promise object is returned when the function is called with test as the parameter.
      when(mockfunc)('test').afterReturn(new Promise<string>((resolve: Function, reject: Function) => {
        console.log("do something");
        resolve('success something');
      }));
      // Execute the function after the Mock operation, that is, execute the defined promise.
      let result = await claser.method_1('test');
      expect(result).assertEqual("success something");// Assert that the execution is successful.
      done();
    })
  })
}
```

**Example code 10**: Use the times/atLeast function to verify the number of times that the mocked function is called.

```ts
import { describe, it, MockKit, when } from '@ohos/hypium'

class ClassName {
  constructor() {
  }

  method_1(...arg: string[]) {
    return '888888';
  }
}
export default function verifyTimesTest() {
  describe('verifyTimesTest', () => {
    it('test_verify_times', 0, () => {
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Initialize the ClassName object claser.
      let claser: ClassName = new ClassName();
      // Mock method_1 of ClassName.
      let func_1: Function = mocker.mockFunc(claser, claser.method_1);
      // Expect the mocked function to return 4.
      when(func_1)('123').afterReturn('4');
      // 5. Invoke the function.
      claser.method_1('123', 'ppp');
      claser.method_1('abc');
      claser.method_1('xyz');
      claser.method_1();
      claser.method_1('abc', 'xxx', 'yyy');
      claser.method_1('abc');
      claser.method_1();
      // Verify that method_1 has been called twice when the parameter is 'abc'.
      mocker.verify('method_1', ['abc']).times(2);// The assertion passes.
       // Verify that method_1 has been called at least twice when the parameter is empty.
      mocker.verify('method_1', []).atLeast(2);// The assertion passes.
    })
  })
}
```

**Example 11:** Mocking a static function (supported since 1.0.16)

```ts
import { describe, it, expect, MockKit, when, ArgumentMatchers } from '@ohos/hypium';

class ClassName {
  constructor() {
  }

  static method_1() {
    return 'ClassName_method_1_call';
  }
}

export default function staticTest() {
  describe('staticTest', () => {
    it('staticTest_001', 0, () => {
      let really_result = ClassName.method_1();
      expect(really_result).assertEqual('ClassName_method_1_call');
      // Create a MockKit object.
      let mocker: MockKit = new MockKit();
      // Mock a function method_1 of the ClassName object.
      let func_1: Function = mocker.mockFunc(ClassName, ClassName.method_1);
      // Mock the function to return mock_data.
      when(func_1)(ArgumentMatchers.any).afterReturn('mock_data');
      let mock_result = ClassName.method_1();
      expect(mock_result).assertEqual('mock_data');// Assertion passed.
      // Disable the mock capability.
      mocker.clear(ClassName);
      let really_result1 = ClassName.method_1();
      expect(really_result1).assertEqual('ClassName_method_1_call');// Assertion passed.
    })
  })
}
```

### Data-driven

The data-driven capability of the unit test framework is supported since [version 1.0.2](https://ohpm.openharmony.cn/#/en/detail/@ohos%2Fhypium). You can reuse test case code, configure input data and expected result data using the data configuration file, and obtain data to implement the corresponding implementation and assertion processing in the test case implementation to reduce redundant test code.

Data-driven capability can drive the number of test case execution times and the parameters passed each time based on the test data configuration. The data.json configuration file is required. The file content is as follows:

>**NOTE**
>
> data.json must be stored in the same directory as the test case file in the *.test.js* or .test.ets format.
>
> The parameter configuration name in data.json must be the same as the parameter name defined in the test case.

```json
{
	"suites": [{
		"describe": ["AbilityTest"],
		"stress": 2,
		"params": {
			"suiteParams1": "suiteParams001",
			"suiteParams2": "suiteParams002"
		},
		"items": [{
			"it": "testDataDriverAsync",
			"stress": 2,
			"params": [{
				"name": "tom",
				"value": 5
			}, {
				"name": "jerry",
				"value": 4
			}]
		}, {
			"it": "testDataDriver",
			"stress": 3
		}]
	}]
}
```

Configuration parameters

| Configuration Item| Description                                 | Mandatory|
| :--------- | :------------------------------------ | ---- |
|  "suite"    | Test suite configuration.                        | Yes  |
|  "describe"    | Test suite name.                      | Yes  |
|  "items" | Test case.                        | Yes  |
|  "it"       | Test case name.                      | Yes  |
|  "params"   | Parameters that can be passed to the test suite or test case.| No  |
|  "stress"   | Number of times that a test suite or test case is executed.    | No  |

**Sample Code**

- Stage Model

Import data.json to the TestAbility.ets file in the TestAbility directory of the test project, and set parameter data before the Hypium.hypiumTest() function is executed. The following is a code example:

- FA Model

Import data.json to the app.js or app.ets file in the TestAbility directory of the test project, and set parameter data before the Hypium.hypiumTest() function is executed. The following is a code example:

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { Hypium } from '@ohos/hypium';
import testsuite from '../test/List.test';// Import the test case set file.
import data from '../test/data.json';// Import the parameter data file.

...
let abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
let abilityDelegatorArguments = abilityDelegatorRegistry.getArguments();
Hypium.setData(data);// Set the parameter data.
Hypium.hypiumTest(abilityDelegator, abilityDelegatorArguments, testsuite);
...
```

```ts
 import { describe, it } from '@ohos/hypium';

 export default function abilityTest() {
  describe('AbilityTest', () => {
    it('testDataDriverAsync', 0, async (done: Function, data: ParmObj) => {
      console.info('name: ' + data.name);
      console.info('value: ' + data.value);
      done();
    });

    it('testDataDriver', 0, () => {
      console.info('stress test');
    })
  })
}
 interface ParmObj {
   name: string,
   value: string
 }
```
>**NOTE**
>
>To use the data-driven parameter input function, the `func` of the test case `it` must be passed with two parameters. `done` is defined in the front, and `data` is defined in the back. If the data-driven parameter input function is not used, you can pass no parameter or only `done` to `func`.

### Capabilities
Special capabilities provide script execution configuration capabilities, including filtering, stress, and random execution. The scripts are executed in CLI mode.

## FAQs About the Unit Test Framework

**What should I do if logs in the test case are printed after the test case result?**

**Description**

The log information added to the test case is not displayed during the execution but is displayed after the execution.

**Possible Causes**

This problem occurs only when the test case calls an asynchronous API. To ensure that logs correctly capture the execution process, all log information in the test case must be printed before the test case execution is complete.

**Solution**

If more than two asynchronous APIs are called, you are advised to encapsulate the API calls into a promise.

**What should I do if a timeout error is reported during case execution?**

**Description**

After the test case execution is complete, the console displays the error message "execute time XXms", indicating that the case execution times out.

**Possible Causes**

1. If the done function is not called when the test case executes an asynchronous API, the test case cannot end normally and finally times out.
2. The function called by the test case takes a long time, which exceeds the timeout interval (5000 ms by default) set for the test case execution.
3. An exception is thrown when the assertion fails during function calling, causing the test case execution to time out and stop. 

**Solution**

1. Check the test case code logic to ensure that the done function can be executed when the assertion fails.
2. You can modify the test case execution timeout parameter in Run/Debug Configurations of DevEco Studio to avoid execution timeout.
3. Check the test case code logic to ensure that the assertion passes.
