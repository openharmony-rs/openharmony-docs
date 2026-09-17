# getAbilityDelegator

## Modules to Import

```TypeScript
```

## getAbilityDelegator

```TypeScript
function getAbilityDelegator(): AbilityDelegator
```

Obtains the **AbilityDelegator** object of the application.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAbilityDelegator](arkts-test-abilitydelegatorregistry-getabilitydelegator-f.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| [AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md) | [AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md) object, which can be used to schedule functions related to the test framework. |

**Examples**

```TypeScript
import AbilityDelegatorRegistry from '@ohos.application.abilityDelegatorRegistry';

let abilityDelegator = AbilityDelegatorRegistry.getAbilityDelegator();
```
