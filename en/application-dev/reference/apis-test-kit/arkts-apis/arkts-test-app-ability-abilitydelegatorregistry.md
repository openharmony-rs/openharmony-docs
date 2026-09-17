# @ohos.app.ability.abilityDelegatorRegistry(AbilityDelegatorRegistry)

**AbilityDelegatorRegistry**, a module of the automatic test framework, is used to obtain [AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md) and [AbilityDelegatorArgs](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegatorargs-abilitydelegatorargs-i.md) objects. **AbilityDelegator** provides APIs for creating [AbilityMonitor](../../apis-ability-kit/arkts-apis/arkts-ability-abilitymonitor-i.md) objects, which can be used to listen for ability lifecycle changes. **AbilityDelegatorArgs** provides APIs for obtaining test parameters.

> **NOTE:** 
> 
> The APIs of this module can be used only in [JsUnit](../../../application-test/unittest-guidelines.md).

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAbilityDelegator](arkts-test-abilitydelegatorregistry-getabilitydelegator-f.md) | Obtains an [AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md) object. |
| [getArguments](arkts-test-abilitydelegatorregistry-getarguments-f.md) | Obtains an [AbilityDelegatorArgs](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegatorargs-abilitydelegatorargs-i.md) object. |

### Enums

| Name | Description |
| --- | --- |
| [AbilityLifecycleState](arkts-test-abilitydelegatorregistry-abilitylifecyclestate-e.md) | Enumerates the ability lifecycle states. It can be used in [getAbilityState(ability)](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md#getabilitystate) of [AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md) to return different ability lifecycle states. |

### Types

| Name | Description |
| --- | --- |
| [AbilityDelegator](arkts-test-abilitydelegatorregistry-abilitydelegator-t.md) | Represents the **AbilityDelegator** module. |
| [AbilityDelegatorArgs](arkts-test-abilitydelegatorregistry-abilitydelegatorargs-t.md) | Represents the **AbilityDelegatorArgs** module. |
| [AbilityMonitor](arkts-test-abilitydelegatorregistry-abilitymonitor-t.md) | Represents the **AbilityMonitor** module. |
| [AbilityStageMonitor](arkts-test-abilitydelegatorregistry-abilitystagemonitor-t.md) | Represents the **AbilityStageMonitor** module. |
| [InteropAbilityMonitor](arkts-test-abilitydelegatorregistry-interopabilitymonitor-t.md) | Provide methods for matching monitored Ability objects that meet specified conditions. The most recently matched Ability objects will be saved in the InteropAbilityMonitor object. |
| [ShellCmdResult](arkts-test-abilitydelegatorregistry-shellcmdresult-t.md) | Represents the **ShellCmdResult** module. |
