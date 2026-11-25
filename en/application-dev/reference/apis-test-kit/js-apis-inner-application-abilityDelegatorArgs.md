# AbilityDelegatorArgs

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=3f4430a1cf9e979027a217e0f6c3b2523fb1862a translatedAt=2026-11-23T07:20:07.960Z pushedAt=2026-11-23T07:28:16.049Z nl=1 -->

**AbilityDelegatorArgs** encapsulates and provides test case parameters, which are obtained by calling [getArguments](js-apis-app-ability-abilityDelegatorRegistry.md#abilitydelegatorregistrygetarguments) in **AbilityDelegatorRegistry**. The parameters include key test parameters such as **bundleName**, **parameters**, and **testCaseNames**. This module provides a standard way to access parameters for test scripts.
 
This module is applicable to scenarios where test parameters need to be obtained for condition judgment or test environment configuration during unit test script writing. Note that the APIs of this module can be used only in the test framework and should not be called in formal service code.

> **Description**
> 
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version. 
> 
> The APIs of this module can be used only in [JsUnit User Guide](https://developer.huawei.com/consumer/en/doc/doccenter-capabilities/unittest-guidelines).

## Modules to Import

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## AbilityDelegatorArgs

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

| Name               | Type                  | Read-Only| Optional| Description                                                        |
| ------------------- | ---------------------- | ---- | ---- | ------------------------------------------------------------ |
| bundleName          | string                 | No   | No   | Bundle name of the app to test. The test framework uses this value to locate and start the target app for testing. |
| parameters          | Record\<string, string> | No   | No   | Parameters of the unit test that is started currently, including the configuration parameters required for running the test. Common key-value pairs include test configurations and running parameters. |
| testCaseNames       | string                 | No   | No   | Names of the test cases to be run, which are used to filter or select the test cases to be executed. You can specify one or more test cases. Multiple test cases are separated by specific separators. |
| testRunnerClassName | string                 | No   | No   | Names of the test case executors. The test framework uses this class to instantiate the test executor. |

**Example**

```ts
// Import the test registration module.
import { abilityDelegatorRegistry } from '@kit.TestKit';

// Obtain the AbilityDelegatorArgs object through AbilityDelegatorRegistry.
let args: abilityDelegatorRegistry.AbilityDelegatorArgs = abilityDelegatorRegistry.getArguments();
```
