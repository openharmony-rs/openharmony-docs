# Ability

```TypeScript
declare class Ability
```

The Ability class is the fundamental unit for application lifecycle scheduling. It is the base class of [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) and [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md), and provides callbacks for system configuration updates and memory level updates. However, you cannot inherit directly from this base class. You should opt for either [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) or [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md) based on your service needs. For details, see [Introduction to Ability Kit](../../../application-models/abilitykit-overview.md).

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## Modules to Import

```TypeScript
import { Ability } from '@kit.AbilityKit';
```

## onConfigurationUpdate

```TypeScript
onConfigurationUpdate(newConfig: Configuration): void
```

Called when a system environment variable changes. You can override this callback to respond to changes in the system environment variables. For example, when the system language changes, the application can perform customized processing in the callback.

> **NOTE:** 
> 
> There are certain restrictions when this callback is actually triggered. For example, if you set the application
> language by calling [setLanguage](arkts-ability-applicationcontext-c.md#setlanguage), the
> system does not trigger the **onConfigurationUpdate** callback even if the system language changes. For details,
> see [When to Use](../../../application-models/subscribe-system-environment-variable-changes.md#when-to-use).
> 
> If you need to monitor the environment variables of the Ability in the page, you can use the
> ApplicationContext.on('environment') method.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newConfig | [Configuration](arkts-ability-app-ability-configuration-configuration-i.md) | Yes | Updated configuration information, including language, color mode, and other system configuration items. |

**Examples**

```TypeScript
// You are not allowed to inherit from the top-level base class Ability. Therefore, the derived class UIAbility is used as an example.
import { UIAbility, Configuration } from '@kit.AbilityKit';

class MyUIAbility extends UIAbility {
  onConfigurationUpdate(config: Configuration) {
    console.info(`onConfigurationUpdate, config: ${JSON.stringify(config)}`);
  }
}
```

## onMemoryLevel

```TypeScript
onMemoryLevel(level: AbilityConstant.MemoryLevel): void
```

Called when the available memory of the entire device changes to a specified level. You can override this callback to respond to changes in the memory level, for example, releasing cached data.

> **NOTE:** 
> 
> Releasing UI components in the **onMemoryLevel** callback may block the main thread tasks of the current process.
> Therefore, you are advised not to release UI components in this callback.
> 
> If you need to monitor the environment variables of the Ability in the page, you can use the
> ApplicationContext.on('environment') method.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | [AbilityConstant.MemoryLevel](arkts-ability-abilityconstant-memorylevel-e.md) | Yes | Level of the available memory.<br>**NOTE:** <br>The trigger conditions may differ across various devices. For example, on a standard device with 12 GB of memory:<br>- When the available memory of the entire device drops to 1700 MB to 1800 MB, the **onMemoryLevel** callback of the MEMORY_LEVEL_MODERATE type is triggered, indicating that the available memory is moderate.<br>- When the available memory of the entire device drops to 1600 MB to 1700 MB, the **onMemoryLevel** callback of the MEMORY_LEVEL_LOW type is triggered, indicating that the available memory is low.<br>- When the available memory of the entire device drops below 1600 MB, the **onMemoryLevel** callback of the MEMORY_LEVEL_CRITICAL type is triggered, indicating that the available memory is critically low. |

**Examples**

```TypeScript
// You are not allowed to inherit from the top-level base class Ability. Therefore, the derived class UIAbility is used as an example.
import { UIAbility, AbilityConstant } from '@kit.AbilityKit';

class MyUIAbility extends UIAbility {
  // Receive the system memory level change callback.
  onMemoryLevel(level: AbilityConstant.MemoryLevel) {
    console.info(`onMemoryLevel, level: ${JSON.stringify(level)}`);
  }
}
```
