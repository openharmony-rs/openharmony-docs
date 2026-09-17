# TestRunner

Base class for the test framework. If you want to implement your own unit test framework, you must inherit this class and overrides all its methods.

**Since:** 8

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

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.
