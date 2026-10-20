# @ohos.app.ability.scriptManager(Script Management)

This module provides the capability to manage and organize script information, and supports reporting the execution results of ArkTS scripts in an app.

> **NOTE:** 
> The ArkTS script of an app must be bound to an ability. Configure the corresponding ability in the
> [skillProfiles tag](../../../quick-start/module-configuration-file.md#skillprofiles) of
> [module.json5](../../../quick-start/module-configuration-file.md).
> The script is exported through export default class. The first parameter of its entry function is fixed as
> [ArkTSScriptInfo](arkts-ability-scriptmanager-arktsscriptinfo-i.md), which is used to receive the script context information passed
> by the system. Developers can add custom parameters after the first parameter.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace scriptManager--><!--Device-unnamed-declare namespace scriptManager-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## Modules to Import

```TypeScript
import { scriptManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [completeArkTSScriptInApp](arkts-ability-scriptmanager-completearktsscriptinapp-f.md#completearktsscriptinapp) | Completes the ArkTS script execution of an app and reports the execution result. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [ArkTSScriptInfo](arkts-ability-scriptmanager-arktsscriptinfo-i.md) | The first parameter of the ArkTS script entry function of an app, used to receive the script context information passed by the system. |
| [ExecuteResult](arkts-ability-scriptmanager-executeresult-i.md) | Defines the result of ArkTS script execution. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ArkTSScriptInfo](arkts-ability-scriptmanager-arktsscriptinfo-i-sys.md) | The first parameter of the ArkTS script entry function of an app, used to receive the script context information passed by the system. |
<!--DelEnd-->
