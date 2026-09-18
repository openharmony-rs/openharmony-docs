# StartOptions

StartOptions can be used as an input parameter for APIs used to launch a UIAbility (for example, [startAbility()](arkts-ability-uiabilitycontext-c.md#startability)). It specifies the options for starting the target UIAbility, including but not limited to the window mode and the display where the target UIAbility is started.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { StartOptions } from '@kit.AbilityKit';
```

## windowFocused

```TypeScript
windowFocused?: boolean
```

Whether the window has focus. The default value is **true**, indicating that the window has focus.

**Constraints**:

1. This property takes effect only on 2-in-1 devices and tablets.
2. This property takes effect only in
[UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability).

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
