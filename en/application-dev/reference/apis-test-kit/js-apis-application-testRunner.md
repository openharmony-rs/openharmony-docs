# @ohos.application.testRunner (TestRunner)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=f49b12145b93fb1a0a3564baf1cfde447ea3a867 translatedAt=2026-07-29T01:31:18.658Z pushedAt=2026-07-30T06:13:47.433Z -->

TestRunner is a basic template class in the automated testing framework. It provides standard APIs for preparing the test environment and running test cases. By inheriting and implementing the **onPrepare()** and **onRun()** methods, you can build custom test execution logic, providing an extensible foundation for the testing framework.

This module is applicable to scenarios where a custom unit testing framework or extended test functions are required. However, it should only be used within the automated testing framework and should not be called in formal service code. If you need to customize the test execution process, you must inherit the class and overwrite all its methods.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> The APIs of this module can be used only in <!--RP1-->[JsUnit](../../application-test/unittest-guidelines.md)<!--RP1End-->.

## Modules to Import

```ts
import { TestRunner } from '@kit.TestKit';
```

## TestRunner

**TestRunner** is a template for the unit test framework. You can inherit this class and override all its methods to customize the unit test framework.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| onStop | [OnStopFn](#onstopfn) | No| Yes| Called when the test is complete and before the test environment exits.<br>**Atomic service API:** This API can be used in atomic services since API version 26.0.0.<br>**Since**: 26.0.0<br> **Model restriction**: This API can be used only in the stage model.|

**Example**

```ts
import { TestRunner } from '@kit.TestKit';

// Implement a custom test runner.
export default class UserTestRunner implements TestRunner {
  // Prepare the unit test environment.
  onPrepare() {
    console.info('Trigger onPrepare');
  }

  // Run test cases.
  onRun() {
    console.info('Trigger onRun');
  }

  // Callback processing when the test is complete
  onStop() {
    console.info('Trigger onStop');
  }
}
```

### onPrepare

onPrepare(): void

Prepares the unit test environment to run test cases. This method needs to be overwritten when the **TestRunner** class is inherited.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 11.

**Example**

```ts 
import { TestRunner } from '@kit.TestKit';

// Implement a custom test runner.
export default class UserTestRunner implements TestRunner {
  // Prepare the unit test environment.
  onPrepare() {
    console.info('Trigger onPrepare');
  }

  onRun() {
  }
}
```

### onRun

onRun(): void

Called to run the test case when the test framework starts to execute a test.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 11.

**Example**

```ts
import { TestRunner } from '@kit.TestKit';

// Implement a custom test runner.
export default class UserTestRunner implements TestRunner {
  onPrepare() {
  }

  // Run test cases.
  onRun() {
    console.info('Trigger onRun');
  }
}
```

## OnStopFn

type OnStopFn = () => void

Called when the test is complete and before the test environment exits.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core