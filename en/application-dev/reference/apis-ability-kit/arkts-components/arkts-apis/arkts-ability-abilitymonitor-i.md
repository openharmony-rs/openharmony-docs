# AbilityMonitor

```TypeScript
export interface AbilityMonitor
```

The module provides the capability of listening for lifecycle state changes of a specified [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md). You can use AbilityMonitor as an input parameter of [abilityDelegator.addAbilityMonitor](arkts-ability-abilitydelegator-i.md#addabilitymonitor) to register a listener.

**Since:** 9

<!--Device-unnamed-export interface AbilityMonitor--><!--Device-unnamed-export interface AbilityMonitor-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onAbilityBackground

```TypeScript
onAbilityBackground?: (ability: UIAbility) => void
```

Callback invoked when the UIAbility object transitions to the background.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityMonitor-onAbilityBackground?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onAbilityBackground?: (ability: UIAbility) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes |  |

## onAbilityCreate

```TypeScript
onAbilityCreate?: (ability: UIAbility) => void
```

Callback invoked when the UIAbility object is created.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityMonitor-onAbilityCreate?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onAbilityCreate?: (ability: UIAbility) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes |  |

## onAbilityDestroy

```TypeScript
onAbilityDestroy?: (ability: UIAbility) => void
```

Callback invoked when the UIAbility object is destroyed.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityMonitor-onAbilityDestroy?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onAbilityDestroy?: (ability: UIAbility) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes |  |

## onAbilityForeground

```TypeScript
onAbilityForeground?: (ability: UIAbility) => void
```

Callback invoked when the UIAbility object transitions to the foreground.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityMonitor-onAbilityForeground?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onAbilityForeground?: (ability: UIAbility) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes |  |

## onWindowStageCreate

```TypeScript
onWindowStageCreate?: (ability: UIAbility) => void
```

Callback invoked when a WindowStage instance is created.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityMonitor-onWindowStageCreate?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onWindowStageCreate?: (ability: UIAbility) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes |  |

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy?: (ability: UIAbility) => void
```

Callback invoked when the WindowStage instance is destroyed.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityMonitor-onWindowStageDestroy?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onWindowStageDestroy?: (ability: UIAbility) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes |  |

## onWindowStageRestore

```TypeScript
onWindowStageRestore?: (ability: UIAbility) => void
```

Callback invoked when the page stack is restored for the target UIAbility during cross-device migration.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityMonitor-onWindowStageRestore?: (ability: UIAbility) => void--><!--Device-AbilityMonitor-onWindowStageRestore?: (ability: UIAbility) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes |  |

## abilityName

```TypeScript
abilityName: string
```

Name of the UIAbility object to be listened.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityMonitor-abilityName: string--><!--Device-AbilityMonitor-abilityName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## moduleName

```TypeScript
moduleName?: string
```

Module name of the UIAbility object.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AbilityMonitor-moduleName?: string--><!--Device-AbilityMonitor-moduleName?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function onAbilityCreateCallback(data: UIAbility) {
  console.info(`onAbilityCreateCallback, data: ${JSON.stringify(data)}`);
}

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityname',
  moduleName: 'moduleName',
  onAbilityCreate: onAbilityCreateCallback
}

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.addAbilityMonitor(monitor, (error: BusinessError) => {
  if (error) {
    console.error(`Failed to add ability monitor. Code: ${error.code}, message: ${error.message}`);
  }
});
```
