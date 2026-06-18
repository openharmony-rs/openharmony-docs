# ShellCmdResult

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->
<!-- md-trans-meta sourceCommit=7b96ce2cdc47279f6264c88642e4fd07a8682bf6 translatedAt=2026-06-18T03:36:59.542Z pushedAt=2026-06-18T07:24:16.922Z -->

The **ShellCmdResult** module provides the shell command execution result.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> The APIs of this module can be used only in <!--RP1-->[JsUnit](../../application-test/unittest-guidelines.md)<!--RP1End-->.

## Modules to Import

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## Usage

Obtain the result through the [executeShellCommand](js-apis-inner-application-abilityDelegator.md#executeshellcommand) method in **abilityDelegator**.

**Example:**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let cmd = 'cmd';

abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.executeShellCommand(cmd, (error: BusinessError, data) => {
  if (error) {
    console.error(`executeShellCommand fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`executeShellCommand success, data: ${JSON.stringify(data)}`);
  }
});
```

## ShellCmdResult

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name     | Type  | Read-Only| Optional| Description                                                        |
| --------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| stdResult | string | No  | No  | Standard output of the shell command.|
| exitCode  | number | No  | No  | Result code of the shell command.|