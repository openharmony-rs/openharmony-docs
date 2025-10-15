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

## Modules to Import

```ts
import { TestRunner } from '@kit.TestKit';
```

## TestRunner.onPrepare

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



## TestRunner.onRun

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
