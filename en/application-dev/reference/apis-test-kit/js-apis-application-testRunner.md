# @ohos.application.testRunner (TestRunner)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The **TestRunner** module provides a test framework. You can use the APIs of this module to prepare the unit test environment and run test cases.

To implement your own unit test framework, extend this class and override its APIs.

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

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| onPrepare | [OnPrepareFn](#onpreparefn23) | No   | No   | Prepares the unit test environment to run test cases.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**NOTE**<br>Since API version 23, the original **onPrepare()** API is changed to a property, but its usage remains unchanged.|
| onRun | [OnRunFn](#onrunfn23) | No   | No   | Runs all test cases.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**NOTE**<br>Since API version 23, the original **onRun()** API is changed to a property, but its usage remains unchanged.|

## OnPrepareFn<sup>23+</sup>

type OnPrepareFn = () => void

Triggered when the unit test environment is ready.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 23.

**Example**

```ts
import { TestRunner } from '@kit.TestKit';

export default class UserTestRunner implements TestRunner {
  onPrepare() {
    console.info('Trigger onPrepare');
  }

  onRun() {
  }
}
```

## OnRunFn<sup>23+</sup>

type OnRunFn = () => void

Triggered when the test case is executed.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 23.

**Example**

```ts
import { TestRunner } from '@kit.TestKit';

export default class UserTestRunner implements TestRunner {
  onPrepare() {
  }

  onRun() {
    console.info('Trigger onRun');
  }
}
```
