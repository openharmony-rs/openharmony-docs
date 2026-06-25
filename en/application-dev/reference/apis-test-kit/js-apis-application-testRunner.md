# @ohos.application.testRunner (TestRunner)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

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

**TestRunner** is a template for the unit test framework. You can inherit this class and override all its methods to customize the unit test framework.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| onStop | [OnStopFn](#onstopfn) | No| Yes| Called when the test is complete and before the test environment exits.<br>**Atomic service API:** This API can be used in atomic services since API version 26.0.0.<br>**Since**: 26.0.0<br> **Model restriction**: This API can be used only in the stage model.|

**Example**

```ts
import { TestRunner } from '@kit.TestKit';

export default class UserTestRunner implements TestRunner {
  onPrepare() {
    console.info('Trigger onPrepare');
  }

  onRun() {
    console.info('Trigger onRun');
  }

  onStop() {
    console.info('Trigger onStop');
  }
}
```

### onPrepare

onPrepare(): void

Prepares the unit test environment to run test cases.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 11.

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

### onRun

onRun(): void

Runs test cases.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 11.

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

## OnStopFn

type OnStopFn = () => void

Called when the test is complete and before the test environment exits.

 **Since**: 26.0.0
 
 **Atomic service API**: This API can be used in atomic services since API version 26.0.0.
 
 **Model restriction**: This API can be used only in the stage model.

 **System capability**: SystemCapability.Ability.AbilityRuntime.Core
