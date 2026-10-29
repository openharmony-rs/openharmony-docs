# AbilityDelegatorArgs

```TypeScript
export interface AbilityDelegatorArgs
```

The **AbilityDelegatorArgs** module provides APIs to obtain an **AbilityDelegatorArgs** object during the execution of test cases.

> **NOTE:** 
> 
> The APIs of this module can be used only in [JsUnit](../../../application-test/unittest-guidelines.md).

**Since:** 8

<!--Device-unnamed-export interface AbilityDelegatorArgs--><!--Device-unnamed-export interface AbilityDelegatorArgs-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application to test.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AbilityDelegatorArgs-bundleName: string--><!--Device-AbilityDelegatorArgs-bundleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters: Record<string, string>
```

Parameters of the unit test that is started currently.

**Type:** Record&lt;string, string&gt;

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AbilityDelegatorArgs-parameters: Record<string, string>--><!--Device-AbilityDelegatorArgs-parameters: Record<string, string>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## testCaseNames

```TypeScript
testCaseNames: string
```

Test case name.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AbilityDelegatorArgs-testCaseNames: string--><!--Device-AbilityDelegatorArgs-testCaseNames: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## testRunnerClassName

```TypeScript
testRunnerClassName: string
```

Names of the test case executors.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AbilityDelegatorArgs-testRunnerClassName: string--><!--Device-AbilityDelegatorArgs-testRunnerClassName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
// Import the test registration module.
import { abilityDelegatorRegistry } from '@kit.TestKit';

// Obtain the AbilityDelegatorArgs object through AbilityDelegatorRegistry.
let args: abilityDelegatorRegistry.AbilityDelegatorArgs = abilityDelegatorRegistry.getArguments();
```
