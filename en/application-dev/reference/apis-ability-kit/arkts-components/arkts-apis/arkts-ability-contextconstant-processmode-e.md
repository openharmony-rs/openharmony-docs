# ProcessMode

Enumerates the process modes of the UIAbility after it is started. As a property of [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md), **ProcessMode** takes effect only in [UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability) and is used to specify the process mode of the target UIAbility. This value takes effect only on 2-in-1 devices and tablets. If it is used on other devices, error code 801 is returned.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## NEW_PROCESS_ATTACH_TO_PARENT

```TypeScript
NEW_PROCESS_ATTACH_TO_PARENT = 1
```

A new process is created, the UIAbility is started on the process, and the process exits along with the parent process.

**Constraints**:

In this mode, the target UIAbility and caller must be in the same application.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM

```TypeScript
NEW_PROCESS_ATTACH_TO_STATUS_BAR_ITEM = 2
```

A new process is created, the UIAbility is started on the process, and the process is bound to the status bar icon.

**Constraints**:

In this mode, the target UIAbility and caller must be in the same application, and the application must have an icon in the status bar.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## ATTACH_TO_STATUS_BAR_ITEM

```TypeScript
ATTACH_TO_STATUS_BAR_ITEM = 3
```

The UIAbility is started, and the process of the UIAbility is bound to the status bar icon.

**Constraints**:

In this mode, the target UIAbility and caller must be in the same application, and the application must have an icon in the status bar.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
