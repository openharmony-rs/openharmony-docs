# AccessibilityActionOptions

```TypeScript
declare interface AccessibilityActionOptions
```

Defines optional parameters for accessibility operations of a component, which is used to restrict or modify the operations initiated by accessibility apps such as the screen reader. This API is supported only by the [Slider](../arkts-components/arkts-arkui-slider-comp.md#slider) component. If this API is used on other components, compilation succeeds but the API does not take effect.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scrollStep

```TypeScript
scrollStep?: number
```

Operation step count for an accessibility scroll action triggered by an accessibility gesture. The default value is determined by the component. This setting does not take effect on unsupported components. Currently, the [Slider](../arkts-components/arkts-arkui-slider-comp.md#slider) component is supported. This API triggers sliding for the **Slider** component through swipe gestures after the component gains focus. Scrolling distance: scrollStep * [step](../arkts-components/arkts-arkui-slider-comp-slideroptions-i.md). The default value is **1**. Out-of-range values fall back to **1**. For non-integer values within the valid range, the value is rounded down to the nearest integer.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
