# OnFillSuccessFn

```TypeScript
type OnFillSuccessFn = (viewData: ViewData) => void
```

Called when auto fill request is successfully handled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| viewData | [ViewData](arkts-ability-autofillmanager-viewdata-t.md) | Yes | View data information for AutoFill. |
