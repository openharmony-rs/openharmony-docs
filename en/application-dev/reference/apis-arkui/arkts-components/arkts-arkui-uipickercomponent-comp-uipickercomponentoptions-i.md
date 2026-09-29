# UIPickerComponentOptions

```TypeScript
declare interface UIPickerComponentOptions
```

Describes the parameters of the **UIPickerComponent** container.

**Since:** 22

<!--Device-unnamed-declare interface UIPickerComponentOptions--><!--Device-unnamed-declare interface UIPickerComponentOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
selectedIndex?: number
```

Index of the selected item, used to specify the initially selected option.

Value range: an integer in [0, number of child components - 1]. If the value is out of range, the default value is used. If a decimal is set, the value is rounded down to an integer.

Default value: **0**. Pass this parameter when the component needs to initially display a specific option.

**Note:** 

When counting child components, child components inside a **Row** container are not counted. A **Row** container and its child components are counted as one child component.

**Type:** number

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-UIPickerComponentOptions-selectedIndex?: number--><!--Device-UIPickerComponentOptions-selectedIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
