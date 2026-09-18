# StartupVisibility

Enumerates the visibility statuses of the UIAbility after it is started. If the target UIAbility is set to invisible, the window of the target UIAbility is not displayed in the foreground, there is no icon in the dock, and the **onForeground** lifecycle of the target UIAbility is not triggered. As a property of [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md), **StartupVisibility** takes effect only in [UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability) and specifies the visibility of the target UIAbility after it is started. This value takes effect only on 2-in-1 devices and tablets. If it is used on other devices, error code 801 is returned.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## STARTUP_HIDE

```TypeScript
STARTUP_HIDE = 0
```

The target UIAbility is hidden after it is started in the new process. The **onForeground** lifecycle of the UIAbility is not invoked.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## STARTUP_SHOW

```TypeScript
STARTUP_SHOW = 1
```

The target UIAbility is displayed normally after it is started in the new process.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
