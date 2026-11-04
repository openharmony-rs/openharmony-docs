# AbilityDelegatorArgs

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->
<!-- md-trans-meta sourceCommit=61ad959070e22c282830a1b55fa1ebaedbcf0ce4 translatedAt=2026-11-04T04:28:21.987Z pushedAt=2026-11-04T10:13:14.957Z nl=1 -->

**AbilityDelegatorArgs** encapsulates and provides test case parameters, which are obtained by calling [getArguments](js-apis-app-ability-abilityDelegatorRegistry.md#abilitydelegatorregistrygetarguments) in **AbilityDelegatorRegistry**. The parameters include key test parameters such as **bundleName**, **parameters**, and **testCaseNames**. This module provides a standard way to access parameters for test scripts.
 
This module is applicable to scenarios where test parameters need to be obtained for condition judgment or test environment configuration during unit test script writing. Note that the APIs of this module can be used only in the test framework and should not be called in formal service code.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version. 
> 
> The APIs of this module can be used only in <!--RP1-->[JsUnit](../../application-test/unittest-guidelines.md)<!--RP1End-->.

## Modules to Import

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## AbilityDelegatorArgs

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

| Name               | Type                  | Read-Only| Optional| Description                                                        |
| ------------------- | ---------------------- | ---- | ---- | ------------------------------------------------------------ |
| bundleName          | string                 | No  | No  | Bundle name of the application to test.|
| parameters          | Record\<string, string> | No  | No  | Parameters of the unit test that is started currently.|
| testCaseNames       | string                 | No  | No  | Test case name.|
| testRunnerClassName | string                 | No  | No  | Names of the test case executors.|

**Example**

```ts
// Import the test registration module.
import { abilityDelegatorRegistry } from '@kit.TestKit';

// Obtain the AbilityDelegatorArgs object through AbilityDelegatorRegistry.
let args: abilityDelegatorRegistry.AbilityDelegatorArgs = abilityDelegatorRegistry.getArguments();
```
