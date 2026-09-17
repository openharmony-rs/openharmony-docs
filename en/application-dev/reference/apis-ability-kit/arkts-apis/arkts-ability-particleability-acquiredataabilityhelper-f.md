# acquireDataAbilityHelper

## Modules to Import

```TypeScript
import { particleAbility } from '@kit.AbilityKit';
```

## acquireDataAbilityHelper

```TypeScript
function acquireDataAbilityHelper(uri: string): DataAbilityHelper
```

Obtains a dataAbilityHelper object.

> **NOTE:** 
> 
> For details about the startup rules for the components in the FA model, see
> [Component Startup Rules (FA Model)](../../../application-models/component-startup-rules-fa.md).
> To access a DataAbility of another application, the target application must be configured with associated
> startup (**AssociateWakeUp** set to **true**).

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.FAModel

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file to open. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityHelper](arkts-ability-dataabilityhelper-dataabilityhelper-i.md) | A utility class used to help other abilities access a DataAbility. |

**Examples**

```TypeScript
import { particleAbility } from '@kit.AbilityKit';

let uri = '';
particleAbility.acquireDataAbilityHelper(uri);
```
