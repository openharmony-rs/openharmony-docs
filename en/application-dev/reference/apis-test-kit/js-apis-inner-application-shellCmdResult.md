# ShellCmdResult

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=f49b12145b93fb1a0a3564baf1cfde447ea3a867 translatedAt=2026-08-07T09:45:28.511Z pushedAt=2026-08-10T02:13:40.217Z -->

**ShellCmdResult** is a data object used to encapsulate the execution result of a shell command in the test framework. It contains two key attributes: **stdResult** (standard output content) and **exitCode** (exit code). This object provides a structured way for test scripts to access the command execution result.

This module is applicable to test scenarios where the execution result of a shell command needs to be verified or the data returned by the command needs to be processed. It is obtained by calling [executeShellCommand](js-apis-inner-application-abilityDelegator.md#executeshellcommand) of **abilityDelegator**. Note that the APIs of this module can be used only in the test framework and should not be called in formal service code.

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

Call [executeShellCommand](js-apis-inner-application-abilityDelegator.md#executeshellcommand) in **abilityDelegator** to obtain a **ShellCmdResult** instance. After the call is successful, a **ShellCmdResult** object is returned, containing the standard result (**stdResult**) and exit code (**exitCode**) of the shell command.

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let shellCommand: string = 'cmd';

// Obtain an AbilityDelegator instance.
abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
// Execute the shell command and obtain the execution result through a callback.
abilityDelegator.executeShellCommand(shellCommand, (error: BusinessError, data) => {
  if (error) {
    console.error(`executeShellCommand fail. Code: ${error.code}, message: ${error.message}`);
  } else {
    console.info(`executeShellCommand success, data: ${JSON.stringify(data)}`);
  }
});
```

## ShellCmdResult

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

| Name     | Type  | Read-Only| Optional| Description                                                        |
| --------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| stdResult | string | No  | No  | Standard output of the shell command.|
| exitCode | number | No | No | Exit code of the shell command. If **0** is returned, the command is executed successfully. If a non-zero value is returned, the command fails to be executed. |