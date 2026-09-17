# ListElement

List element @interface ListElement

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

## rotation

```TypeScript
rotation(obj?: FocusParamObj): void
```

Requests or cancels the crown rotation focus for a component. If focus is set to true, the crown event focus is requested. If focus is set to false, the crown event focus is canceled. This attribute can be defaulted to true.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | [FocusParamObj](arkts-arkui-viewmodel-focusparamobj-i.md) | No | { focus: true &#124; false } |

## scrollTo

```TypeScript
scrollTo(position: ListScrollToOptions): void
```

Scrolls the list to the position of the item at the specified index.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [ListScrollToOptions](arkts-arkui-viewmodel-listscrolltooptions-i.md) | Yes |  |
