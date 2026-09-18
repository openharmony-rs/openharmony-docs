# OnColorModeUpdatedFn

```TypeScript
type OnColorModeUpdatedFn = (colorMode: ConfigurationConstant.ColorMode) => void
```

Defines an OnColorModeUpdatedFn function.

@typedef { function }

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorMode | [ConfigurationConstant.ColorMode](arkts-ability-configurationconstant-colormode-e.md) | Yes | Indicates the system's light or dark color mode |
