# AccessibilityFocusCallback

```TypeScript
declare type AccessibilityFocusCallback = (isFocus: boolean) => void
```

Defines the callback type used in **onAccessibilityFocus**.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-unnamed-declare type AccessibilityFocusCallback = (isFocus: boolean) => void--><!--Device-unnamed-declare type AccessibilityFocusCallback = (isFocus: boolean) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isFocus | boolean | Yes | Whether the component has focus.<br>true: the current component has focus.<br>false: the current component is blurred. |
