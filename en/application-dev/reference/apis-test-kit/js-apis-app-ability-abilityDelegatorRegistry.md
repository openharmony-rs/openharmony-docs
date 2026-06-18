# @ohos.app.ability.abilityDelegatorRegistry (AbilityDelegatorRegistry)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->
<!-- md-trans-meta sourceCommit=7b96ce2cdc47279f6264c88642e4fd07a8682bf6 translatedAt=2026-06-18T03:36:52.239Z pushedAt=2026-06-18T07:24:16.920Z -->

**AbilityDelegatorRegistry**, a module of the automatic test framework, is used to obtain [AbilityDelegator](js-apis-inner-application-abilityDelegator.md) and [AbilityDelegatorArgs](js-apis-inner-application-abilityDelegatorArgs.md) objects. **AbilityDelegator** provides APIs for creating [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md#abilitymonitor-1) objects, which can be used to listen for ability lifecycle changes. **AbilityDelegatorArgs** provides APIs for obtaining test parameters.

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

Enumerates the ability lifecycle states. It can be used in [getAbilityState(ability)](js-apis-inner-application-abilityDelegator.md#getabilitystate9) of [AbilityDelegator](js-apis-inner-application-abilityDelegator.md) to return different ability lifecycle states.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name         | Value  | Description                       |
| ------------- | ---- | --------------------------- |
| UNINITIALIZED | 0    | The ability is in an invalid state.  |
| CREATE        | 1    | The ability is created.|
| FOREGROUND    | 2    | The ability is running in the foreground.  |
| BACKGROUND    | 3    | The ability is running in the background.  |
| DESTROY       | 4    | The ability is destroyed.|

## abilityDelegatorRegistry.getAbilityDelegator

getAbilityDelegator(): AbilityDelegator

Obtains an [AbilityDelegator](js-apis-inner-application-abilityDelegator.md) object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [AbilityDelegator](js-apis-inner-application-abilityDelegator.md) | [AbilityDelegator](js-apis-inner-application-abilityDelegator.md) object, which can be used to schedule the functionalities of the test framework.|

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { Want } from '@kit.AbilityKit';

let abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility'
};

abilityDelegator.startAbility(want, (err) => {
  if (err) {
    console.error(`Failed start ability, error: ${JSON.stringify(err)}`);
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

let args = abilityDelegatorRegistry.getArguments();
console.info(`getArguments bundleName: ${args.bundleName}`);
console.info(`getArguments parameters: ${JSON.stringify(args.parameters)}`);
console.info(`getArguments testCaseNames: ${args.testCaseNames}`);
console.info(`getArguments testRunnerClassName: ${args.testRunnerClassName}`);
```

## AbilityDelegator

type AbilityDelegator = _AbilityDelegator

Provides the ability to listen for and manage [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md) lifecycle changes through [AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) instances. For example, obtaining the current state of a UIAbility (such as whether it has been created or is in the foreground), querying the currently focused UIAbility, waiting for a UIAbility to enter a specific lifecycle node (such as waiting for a UIAbility to enter **onForeground**), starting a specified UIAbility, and setting timeout mechanisms.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityDelegator](js-apis-inner-application-abilityDelegator.md) | The **AbilityDelegator** module.|

## AbilityDelegatorArgs

type AbilityDelegatorArgs = _AbilityDelegatorArgs

Provides the ability to obtain the test case parameter **AbilityDelegatorArgs** object during application test case execution.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityDelegatorArgs](js-apis-inner-application-abilityDelegatorArgs.md) | The **AbilityDelegatorArgs** module.|

## AbilityMonitor

type AbilityMonitor = _AbilityMonitor

Serves as an input parameter for [addAbilityMonitor](../apis-test-kit/js-apis-inner-application-abilityDelegator.md#addabilitymonitor9) in **abilityDelegator** to listen for lifecycle changes of a specified UIAbility.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityMonitor](../apis-ability-kit/js-apis-inner-application-abilityMonitor.md) | The **AbilityMonitor** module.|

## ShellCmdResult

type ShellCmdResult = _ShellCmdResult

Provides the shell command execution result.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_ShellCmdResult](js-apis-inner-application-shellCmdResult.md) | The **ShellCmdResult** module.|

## AbilityStageMonitor<sup>14+</sup>

type AbilityStageMonitor = _AbilityStageMonitor

Provides the ability to listen for a specified [AbilityStage](../apis-ability-kit/js-apis-app-ability-abilityStage.md) object. You can use **AbilityStageMonitor** as an input parameter for [abilityDelegator.waitAbilityStageMonitor](../apis-test-kit/js-apis-inner-application-abilityDelegator.md#waitabilitystagemonitor9) to register a listener.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_AbilityStageMonitor](../apis-ability-kit/js-apis-inner-application-abilityStageMonitor.md) | The **AbilityStageMonitor** module.|