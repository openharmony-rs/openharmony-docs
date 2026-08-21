# @ohos.app.ability.abilityDelegatorRegistry (AbilityDelegatorRegistry)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=aee2f7468d1b3b04e493c7068f7ee7eaa8e0ca32 translatedAt=2026-08-07T09:44:48.034Z pushedAt=2026-08-07T11:30:49.571Z -->

**AbilityDelegatorRegistry**, a module of the automatic test framework, is used to obtain [AbilityDelegator](js-apis-inner-application-abilityDelegator.md) and [AbilityDelegatorArgs](js-apis-inner-application-abilityDelegatorArgs.md)objects. With this module, you can use the [AbilityDelegator](js-apis-inner-application-abilityDelegator.md) object to add a [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md#abilitymonitor-1) object to monitor the lifecycle status changes of a specified ability. In addition, you can use the [AbilityDelegatorArgs](js-apis-inner-application-abilityDelegatorArgs.md) object to read the current test parameters. This module is applicable to automated testing scenarios, which can help you accurately capture lifecycle changes of abilities, improving testing efficiency and accuracy.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> The APIs of this module can be used only in <!--RP1-->[JsUnit](../../application-test/unittest-guidelines.md)<!--RP1End-->.

## Modules to Import

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## AbilityLifecycleState

Enumerates the ability lifecycle states. It can be used in [getAbilityState](js-apis-inner-application-abilityDelegator.md#getabilitystate9) of [AbilityDelegator](js-apis-inner-application-abilityDelegator.md) to return different ability lifecycle states.
**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

| Name         | Value  | Description                       |
| ------------- | ---- | --------------------------- |
| UNINITIALIZED | 0    | The ability is in an invalid state.  |
| CREATE        | 1    | The ability is created.|
| FOREGROUND    | 2    | The ability is running in the foreground.  |
| BACKGROUND    | 3    | The ability is running in the background.  |
| DESTROY       | 4    | The ability is destroyed.|

## abilityDelegatorRegistry.getAbilityDelegator

getAbilityDelegator(): AbilityDelegator

Obtains an [AbilityDelegator](js-apis-inner-application-abilityDelegator.md) object. This object can be used to schedule the test framework and perform related test functions.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [AbilityDelegator](js-apis-inner-application-abilityDelegator.md) | **AbilityDelegator** object used to schedule the functionalities of the test framework. |

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the AbilityDelegator object of the application.
let abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
// Construct a Want parameter to specify the target ability.
let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility'
};

// Start the specified ability.
abilityDelegator.startAbility(want, (err: BusinessError) => {
  if (err) {
    console.error(`Failed start ability. code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Success start ability.');
  }
});
```

## abilityDelegatorRegistry.getArguments

getArguments(): AbilityDelegatorArgs

Obtains an [AbilityDelegatorArgs](js-apis-inner-application-abilityDelegatorArgs.md) object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [AbilityDelegatorArgs](js-apis-inner-application-abilityDelegatorArgs.md) | [AbilityDelegatorArgs](js-apis-inner-application-abilityDelegatorArgs.md) object, which can be used to obtain test parameters.|

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';

// Obtain the AbilityDelegatorArgs object of the application.
let args = abilityDelegatorRegistry.getArguments();
// Print the test parameter information.
console.info(`getArguments bundleName: ${args.bundleName}`);
console.info(`getArguments parameters: ${JSON.stringify(args.parameters)}`);
console.info(`getArguments testCaseNames: ${args.testCaseNames}`);
console.info(`getArguments testRunnerClassName: ${args.testRunnerClassName}`);
```

## AbilityDelegator

type AbilityDelegator = _AbilityDelegator

Provides the capability of listening for and managing the lifecycle changes of [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md) instances through [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instances. For example, you can obtain the current state of a UIAbility (for example, whether the UIAbility has been created or is in the foreground), obtain the UIAbility that currently has the focus, wait for the UIAbility to enter a lifecycle node (for example, the **onForeground** state), start a specified UIAbility, and set the timeout mechanism.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityDelegator](js-apis-inner-application-abilityDelegator.md) | The **AbilityDelegator** module.|

## AbilityDelegatorArgs

type AbilityDelegatorArgs = _AbilityDelegatorArgs

Provides the capability of obtaining an **AbilityDelegatorArgs** object during the execution of test cases.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityDelegatorArgs](js-apis-inner-application-abilityDelegatorArgs.md) | The **AbilityDelegatorArgs** module.|

## AbilityMonitor

type AbilityMonitor = _AbilityMonitor

Serves as an input parameter of [addAbilityMonitor](../apis-test-kit/js-apis-inner-application-abilityDelegator.md#addabilitymonitor9) to listen for lifecycle changes of a UIAbility.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | The **AbilityMonitor** module.|

## ShellCmdResult

type ShellCmdResult = _ShellCmdResult

Provides the shell command execution result. It can be used to execute shell commands and obtain the execution result, including the return code and standard output, during automated testing.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_ShellCmdResult](js-apis-inner-application-shellCmdResult.md) | The **ShellCmdResult** module.|

## AbilityStageMonitor<sup>14+</sup>

type AbilityStageMonitor = _AbilityStageMonitor

Provides the capability of listening for a specified [AbilityStage](../apis-ability-kit/js-apis-app-ability-abilityStage.md) object. You can use AbilityStageMonitor as an input parameter of [abilityDelegator.waitAbilityStageMonitor](../apis-test-kit/js-apis-inner-application-abilityDelegator.md#waitabilitystagemonitor9) to register a listener.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | The **AbilityStageMonitor** module.|