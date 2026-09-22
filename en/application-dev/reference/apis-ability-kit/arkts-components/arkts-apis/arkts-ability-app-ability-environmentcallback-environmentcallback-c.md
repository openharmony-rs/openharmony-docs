# EnvironmentCallback

```TypeScript
export default class EnvironmentCallback
```

The EnvironmentCallback module provides capabilities to listen for system environment changes.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { EnvironmentCallback } from '@kit.AbilityKit';
```

## onConfigurationUpdated

```TypeScript
onConfigurationUpdated(config: Configuration): void
```

Called when the system configuration changes, after [a listener has been registered for such events](arkts-ability-applicationcontext-c.md#onenvironment).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [Configuration](arkts-ability-app-ability-configuration-configuration-i.md) | Yes | Configuration object after the change. |

**Examples**

See Usage of EnvironmentCallback.

## onMemoryLevel

```TypeScript
onMemoryLevel(level: AbilityConstant.MemoryLevel): void
```

Called when the system memory level changes, after [a listener has been registered for such events](arkts-ability-applicationcontext-c.md#onenvironment).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | [AbilityConstant.MemoryLevel](arkts-ability-abilityconstant-memorylevel-e.md) | Yes | Memory level, indicating the available memory of the entire device. |

**Examples**

See Usage of EnvironmentCallback.
