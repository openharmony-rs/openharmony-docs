# UIPickerComponentOptions

Describes the parameters of the **UIPickerComponent** container.

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
selectedIndex?: number
```

Index of the selected item.

Value range: an integer in the range of [0, Number of child components – 1]. If the value is not within the value range, the default value is used. If a decimal number is set, the integer part after rounding down is used.

Default value: 0

NOTE

When counting the number of child components, the **Row** container and its child components are counted as one child component.

**Type:** number

**Default:** 0

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
