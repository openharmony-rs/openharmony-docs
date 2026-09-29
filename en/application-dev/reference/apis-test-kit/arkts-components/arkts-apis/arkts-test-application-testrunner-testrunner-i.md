# TestRunner

```TypeScript
interface TestRunner
```

Base class for the test framework. If you want to implement your own unit test framework, you must inherit this class and overrides all its methods.

**Since:** 8

<!--Device-unnamed-interface TestRunner--><!--Device-unnamed-interface TestRunner-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { TestRunner } from '@kit.TestKit';
```

## onPrepare

```TypeScript
onPrepare(): void
```

Prepare the unit testing environment for running test cases.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TestRunner-onPrepare(): void--><!--Device-TestRunner-onPrepare(): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

**Examples**

```TypeScript
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

## onRun

```TypeScript
onRun(): void
```

Run all test cases.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TestRunner-onRun(): void--><!--Device-TestRunner-onRun(): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

**Examples**

```TypeScript
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

## onStop

```TypeScript
onStop?: OnStopFn
```

Stop all test cases.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-TestRunner-onStop?: OnStopFn--><!--Device-TestRunner-onStop?: OnStopFn-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

**Examples**

```TypeScript
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
