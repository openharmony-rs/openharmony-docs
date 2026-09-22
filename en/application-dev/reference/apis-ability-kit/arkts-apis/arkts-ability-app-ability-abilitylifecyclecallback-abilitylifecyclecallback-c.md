# AbilityLifecycleCallback

```TypeScript
declare class AbilityLifecycleCallback
```

The lifecycle of a [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) dynamically changes from creation to destruction. The AbilityLifecycleCallback module provides the capability to listen for these lifecycle changes, which can be used for scenarios such as tracking the runtime duration of each UIAbility and performing data loading decoupled from the service logic of UIAbility.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## Modules to Import

```TypeScript
import { AbilityLifecycleCallback } from '@kit.AbilityKit';
```

## onAbilityBackground

```TypeScript
onAbilityBackground(ability: UIAbility): void
```

Called after the [onBackground](arkts-ability-app-ability-uiability-uiability-c.md#onbackground) callback of the UIAbility is triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilityContinue

```TypeScript
onAbilityContinue(ability: UIAbility): void
```

Called after the [onContinue](arkts-ability-app-ability-uiability-uiability-c.md#oncontinue) callback of the UIAbility is triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilityCreate

```TypeScript
onAbilityCreate(ability: UIAbility): void
```

Called after the [onCreate](arkts-ability-app-ability-uiability-uiability-c.md#oncreate) callback of the UIAbility is triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilityDestroy

```TypeScript
onAbilityDestroy(ability: UIAbility): void
```

Called after the [onDestroy](arkts-ability-app-ability-uiability-uiability-c.md#ondestroy) callback of the UIAbility is triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilityForeground

```TypeScript
onAbilityForeground(ability: UIAbility): void
```

Called after the [onForeground](arkts-ability-app-ability-uiability-uiability-c.md#onforeground) callback of the UIAbility is triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilitySaveState

```TypeScript
onAbilitySaveState?(ability: UIAbility): void
```

Called after the [onSaveState](arkts-ability-app-ability-uiability-uiability-c.md#onsavestate) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilityWillBackground

```TypeScript
onAbilityWillBackground?(ability: UIAbility): void
```

Called before the [onBackground](arkts-ability-app-ability-uiability-uiability-c.md#onbackground) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilityWillContinue

```TypeScript
onAbilityWillContinue?(ability: UIAbility): void
```

Called before the [onContinue](arkts-ability-app-ability-uiability-uiability-c.md#oncontinue) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilityWillCreate

```TypeScript
onAbilityWillCreate?(ability: UIAbility): void
```

Called before the [onCreate](arkts-ability-app-ability-uiability-uiability-c.md#oncreate) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilityWillDestroy

```TypeScript
onAbilityWillDestroy?(ability: UIAbility): void
```

Called before the [onDestroy](arkts-ability-app-ability-uiability-uiability-c.md#ondestroy) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilityWillForeground

```TypeScript
onAbilityWillForeground?(ability: UIAbility): void
```

Called before the [onForeground](arkts-ability-app-ability-uiability-uiability-c.md#onforeground) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onAbilityWillSaveState

```TypeScript
onAbilityWillSaveState?(ability: UIAbility): void
```

Called before the [onSaveState](arkts-ability-app-ability-uiability-uiability-c.md#onsavestate) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onNewWant

```TypeScript
onNewWant?(ability: UIAbility): void
```

Called after the [onNewWant](arkts-ability-app-ability-uiability-uiability-c.md#onnewwant) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onWillNewWant

```TypeScript
onWillNewWant?(ability: UIAbility): void
```

Called before the [onNewWant](arkts-ability-app-ability-uiability-uiability-c.md#onnewwant) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onWindowStageActive

```TypeScript
onWindowStageActive(ability: UIAbility, windowStage: window.WindowStage): void
```

Called when the main window of the UIAbility gains focus.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |
| windowStage | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | Yes | Main window manager of the UIAbility associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onWindowStageCreate

```TypeScript
onWindowStageCreate(ability: UIAbility, windowStage: window.WindowStage): void
```

Called after the [onWindowStageCreate](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagecreate) callback of the UIAbility is triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |
| windowStage | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | Yes | Main window manager of the UIAbility associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onWindowStageDestroy

```TypeScript
onWindowStageDestroy(ability: UIAbility, windowStage: window.WindowStage): void
```

Called after the [onWindowStageDestroy](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagedestroy) callback of the UIAbility is triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |
| windowStage | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | Yes | Main window manager of the UIAbility associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onWindowStageInactive

```TypeScript
onWindowStageInactive(ability: UIAbility, windowStage: window.WindowStage): void
```

Called when the main window of the UIAbility loses focus.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |
| windowStage | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | Yes | Main window manager of the UIAbility associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onWindowStageRestore

```TypeScript
onWindowStageRestore?(ability: UIAbility, windowStage: window.WindowStage): void
```

Called after the [onWindowStageRestore](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagerestore) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |
| windowStage | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | Yes | Main window manager of the UIAbility associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onWindowStageWillCreate

```TypeScript
onWindowStageWillCreate?(ability: UIAbility, windowStage: window.WindowStage): void
```

Called before the [onWindowStageCreate](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagecreate) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |
| windowStage | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | Yes | Main window manager of the UIAbility associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onWindowStageWillDestroy

```TypeScript
onWindowStageWillDestroy?(ability: UIAbility, windowStage: window.WindowStage): void
```

Called before the [onWindowStageDestroy](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagedestroy) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |
| windowStage | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | Yes | Main window manager of the UIAbility associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.

## onWindowStageWillRestore

```TypeScript
onWindowStageWillRestore?(ability: UIAbility, windowStage: window.WindowStage): void
```

Called before the [onWindowStageRestore](arkts-ability-app-ability-uiability-uiability-c.md#onwindowstagerestore) callback of the UIAbility is triggered.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | Yes | UIAbility object associated with the callback event. |
| windowStage | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | Yes | Main window manager of the UIAbility associated with the callback event. |

**Examples**

For details, see AbilityLifecycleCallback Usage Example.
