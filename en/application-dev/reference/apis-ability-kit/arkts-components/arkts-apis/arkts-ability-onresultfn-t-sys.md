# OnResultFn (System API)

```TypeScript
type OnResultFn = (parameter: AbilityResult) => void
```

Defines a onResult function.

@typedef { function } OnResultFn

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.VerticalPanel

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | Yes | The Parameter returned if the UIExtensionAbility call terminateSelfWithResult. |
