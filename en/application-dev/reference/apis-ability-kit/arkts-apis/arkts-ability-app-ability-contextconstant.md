# @ohos.app.ability.contextConstant(Context-related Constants)

The ContextConstant module defines context-related enums, including the file encryption partition level and process mode of the UIAbility after it is started.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { contextConstant } from '@kit.AbilityKit';
```

## Summary

### Enums

| Name | Description |
| --- | --- |
| [AreaMode](arkts-ability-contextconstant-areamode-e.md) | Enumerates the file encryption levels, which are used to ensure data security for applications across different scenarios. You can select the appropriate encryption level based on the application requirements to protect user data. |
| [ContextType](arkts-ability-contextconstant-contexttype-e.md) | Context type |
| [ProcessMode](arkts-ability-contextconstant-processmode-e.md) | Enumerates the process modes of the UIAbility after it is started. As a property of [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md), **ProcessMode** takes effect only in [UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability-1) and is used to specify the process mode of the target UIAbility. This value takes effect only on 2-in-1 devices and tablets. If it is used on other devices, error code 801 is returned. |
| [Scenarios](arkts-ability-contextconstant-scenarios-e.md) | Enumerates the scenarios where the [onNewWant](arkts-ability-app-ability-uiability-uiability-c.md#onnewwant) lifecycle callback is not triggered. It is used in the [setOnNewWantSkipScenarios](arkts-ability-uiabilitycontext-c.md#setonnewwantskipscenarios) API. |
| [StartupVisibility](arkts-ability-contextconstant-startupvisibility-e.md) | Enumerates the visibility statuses of the UIAbility after it is started. If the target UIAbility is set to invisible, the window of the target UIAbility is not displayed in the foreground, there is no icon in the dock, and the **onForeground** lifecycle of the target UIAbility is not triggered. As a property of [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md), **StartupVisibility** takes effect only in [UIAbilityContext.startAbility](arkts-ability-uiabilitycontext-c.md#startability-1) and specifies the visibility of the target UIAbility after it is started. This value takes effect only on 2-in-1 devices and tablets. If it is used on other devices, error code 801 is returned. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ContextType](arkts-ability-contextconstant-contexttype-e-sys.md) | Context type |
<!--DelEnd-->
