# OnUIPickerComponentCallback

```TypeScript
declare type OnUIPickerComponentCallback = (selectedIndex: number) => void
```

Defines the callback type for the [onChange](arkts-arkui-uipickercomponent-comp-attribute.md#onchange) and [onScrollStop](arkts-arkui-uipickercomponent-comp-attribute.md#onscrollstop) events.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-unnamed-declare type OnUIPickerComponentCallback = (selectedIndex: number) => void--><!--Device-unnamed-declare type OnUIPickerComponentCallback = (selectedIndex: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedIndex | number | Yes | Index of the currently selected item.<br>Value range: an integer in [0, number of child components - 1]. |
